# Brightway strategic development plan

This document summarizes the changes needed to get Brightway version 3 to a stable release. Version 3 brings stability and flexibility to the Brightway ecosystem - the core components are fixed, and will not significantly change in the future. They can also be more easily adapted, as they each have defined and standardized interfaces with each other.

Brightway 3 should have the following core libraries:

* `bw_default_db` (name TBD; based on `bw2data`)
* `bw_projects` (based on parts of `bw2data`)
* `bw_calc` (based on `bw2calc`)
* `bw_processing` (already done; docs and tests could be improved)
* `matrix_utils` (already done; docs and tests could be improved)
* `bw_io` (based on `bw2io`)
* `bw_analysis` (based on `bw2analyzer`)

Brightway 3 needs to satisfy these key user needs:

* Dispatch calculations to cloud workers
* Use alternative databases and schemas
* Use IO without other Brightway components as part of an ETL pipeline

## Separate `bw_calc`

This is already quite advanced. Specific tasks:

* Updating `presamples` or porting concept of campaigns to another library (or `bw2data` calculation setups) to allow easier management of datapackages
* Integrated documentation
* Provide equivalent of `ComparativeMonteCarlo`

Nice-to-have:

* Standard report format for calculation results
* Packaging/scripts (plus containerization) to easily get calculation running on web servers
* Web API (e.g. Flask app) for running calculations
* Provide support for multiple impact categories in one calculation

## Brightway Common Database API

One big barrier to adapting Brightway to other databases is its tight coupling between projects, the default database backend, and the IO library. To decouple these, we first need to define *data formats*, *interfaces*, and *endpoints*.

The interface is easy to define - we will use Python, with normal data structures, either built in or with [attrs](https://www.attrs.org/en/stable/index.html).

The data format will be [eILCD](https://eplca.jrc.ec.europa.eu/LCDN/developerILCDDataFormat.xhtml). eILCD is an XML format for life cycle inventory and impact category data. We are choosing eILCD instead of developing something on our own, or using another existing format, because:

* eILCD is the only format really battle tested with multiple implementations and use in a variiety of contexts
* eILCD is the transfer format for GLAD and PEF
* eILCD is extensively documented, both with XSD and guidance

Don't get the wrong impression, eILCD is everything you hate about XML, but arguably even worse as it was mostly designed by scientists instead of programmers.

The hardest part are the API endpoints. These are the Python methods or functions which programs can use to interface with any database backend that follow the Brightway common database standard; database implementors can choose to only support part of this standard, but we should define this standard in a parsimonious fashion, such that open source implementations choose to implement the whole standard.

Based on the current default database backend, the following CRUD endpoints should be considered:

* Node
* Edge
* Impact category
* Characterization factor

It might also be necessary to have a common endpoint for `bw_projects` for when a project is activated.

After finishing this section, programmers will be able to choose whatever database and schema they want, and will know exactly which functions are expected by `bw_io` such that the IO classes can write or update data. There will also be a reference implementation, compatible with existing `bw2data` code and semantics, which will demonstrate how users can import data from `bw_io`, and query data from an ORM.

Specific tasks:

* Adapt eILCD to standard Python data structures. Any deviations from eILCD nomenclature or structures must be documented and justified.
* Design a set of Python signals to be emitted by database backends on CRUD operations. This is needed for search indices or other integrated platforms.
* Specify and provide reference implementation of Brightway Common Database standard
* Port `bw2data` to the standard as `bw_data`

Nice-to-have:

* Reference implementation against a different type of database

## Smaller `bw2data` updates

### Make `projects` optional

Projects as separate subdirectories is not a useful concept for all databases or organizations. Rather, they are an implementation detail of the current database backend structure (separate SQLite databases in subdirectories).

Specific tasks:

* Separate project handling into a separate library
* Adapt testing framework to not rely on projects
* Provide separate test decorators for backends which do and do not use the projects concept

### Switch all data storage in `bw2data` to SQLite

We now have an evil mix of pickle files, JSON files, and SQLite databases. It is very, very dumb. The original justification was that loading 500.000 locations codes (during regionalized LCA) was much faster in one file than a big database query, and JSON allowed configurations to be edited without having to know how to use a relational database. These reasons are inadequate.

Specific tasks:

* Migrate all data storage in `bw2data` to SQLite databases.

Nice-to-have:

* Use the SQLite text search instead of a separate Whoosh search index.

## ILCD as standard interface between `bw_data` and `bw_io`

The current interface between `bw2data` and `bw2io` is inadequate - it does not include a lot of important metadata, it grew organically without clear design or vision, it doesn't not distinguish between inventory and impact assessment, and it barely specified and therefore impossible to implement by outside collaborators.

Specific tasks:

* `bw_io` needs to to support the Brightway Common Database standard
* `bw_io` strategies need to be rewritten to use the ported ILCD data standard internally. Probably it makes sense to first have a single wrapping decorator and then port individual strategies when possible.
