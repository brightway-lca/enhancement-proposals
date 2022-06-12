# Brightway strategic development plan

This document summarizes the changes needed to get Brightway version 3 to a stable release. Version 3 brings stability and flexibility to the Brightway ecosystem - the core components are fixed, and will not significantly change in the future. They can also be more easily adapted, as they each have defined and standardized interfaces with each other.

Brightway 3 should have the following core libraries:

* `bw_default_db` (name TBD; based on `bw2data`)
* `bw_projects` (based on parts of `bw2data`)
* `bw_calc` (based on `bw2calc`)
* `bw_processing` ([already done](https://github.com/brightway-lca/bw_processing); docs and tests could be improved)
* `matrix_utils` ([already done](https://github.com/brightway-lca/matrix_utils); docs and tests could be improved)
* `bw_io` (based on `bw2io`)
* `bw_analysis` (based on `bw2analyzer`)

Brightway 3 needs to satisfy these key user needs:

* Dispatch calculations to cloud workers
* Use alternative databases and schemas
* Use IO without other Brightway components as part of an ETL pipeline

The plan is being managed as a [Github project](https://github.com/orgs/brightway-lca/projects/2/views/1)

## [Separate `bw_calc`](https://github.com/brightway-lca/enhancement-proposals/issues/2)

This is already quite advanced. Specific tasks:

* A1 Updating `presamples` or porting concept of campaigns to another library (or `bw2data` calculation setups) to allow easier management of datapackages
* A2 Provide equivalent of `ComparativeMonteCarlo`

Nice-to-have:

* A3 Standard report format for calculation results
* A4 Packaging/scripts (plus containerization) to easily get calculation running on web servers
* A5 Web API (e.g. Flask app) for running calculations, with rate-limited implementation on DdS server
* A6 Provide support and specification for multiple impact categories in one calculation (`MultiLCA`)

## [Brightway Common Database API](https://github.com/brightway-lca/enhancement-proposals/issues/4)

One big barrier to adapting Brightway to other databases is its tight coupling between projects, the default database backend, and the IO library. To decouple these, we first need to define *data formats*, *interfaces*, and *endpoints*.

The interface is easy to define - we will use Python, with normal data structures, either built in or with [attrs](https://www.attrs.org/en/stable/index.html) or similar.

The data format will be [eILCD](https://eplca.jrc.ec.europa.eu/LCDN/developerILCDDataFormat.xhtml). eILCD is an XML format for life cycle inventory and impact category data. We are choosing eILCD instead of developing something on our own, or using a different existing format, because:

* eILCD is the only format really battle tested with multiple implementations and use in a variety of contexts
* eILCD is the transfer format for GLAD and PEF
* eILCD is extensively documented, both with XSD files and guidance

Don't get the wrong impression, eILCD is everything you hate about XML, but arguably even worse than usual as it was mostly designed by scientists instead of programmers. But it is still better than the alternatives.

The hardest part are the API endpoints. These are Python methods or functions which programs can use to interface with any database backend that follow the Brightway common database standard; database implementors can choose to only support part of this standard, but we should define this standard in a parsimonious fashion, such that open source implementations do choose to implement the whole standard.

Based on the current default database backend, the following CRUD endpoints should be considered:

* Node (Can be called activity or process)
* Edge (Can be called exchange)
* Impact category
* Characterization factor

It might also be necessary to have a common endpoint for `bw_projects` for when a project is activated.

After finishing this section, programmers will be able to choose whatever database and schema they want, and will know exactly which functions are expected by `bw_io` such that the IO classes can write or update data. There will also be a reference implementation, compatible with existing `bw2data` code and semantics, which will demonstrate how users can import data from `bw_io`, and query data from an ORM.

Specific tasks:

* B1 Choose, document, and justify the data structures used for passing data following the common API.
* B2 Adapt eILCD to a standard Python data structures. Any deviations from eILCD nomenclature or structures must be documented and justified.
* B3 Design a set of Python signals to be emitted by database backends on CRUD operations. This is needed for search indices or other integrated platforms. Follow Activity Browser signals when possible to maximize compatibility.
* B4 Specify and provide a reference implementation of the Brightway Common Database standard
* B5 Port `bw2data` to the standard as `bw_data`

Nice-to-have:

* B6 Reference common database implementation against a different type of database (e.g. graph database)

## Smaller `bw2data` updates

### Make `projects` optional

Projects as separate subdirectories is not a useful concept for all databases or organizations. Rather, they are an implementation detail of the current database backend structure (separate SQLite databases in subdirectories).

Specific tasks:

* C1 Separate project handling into a separate library
* C2 Adapt testing framework to not rely on projects
* C3 Provide separate test decorators for backends which do and do not use the projects concept

### Switch all data storage in `bw2data` to SQLite

We now have an evil mix of pickle files, JSON files, and SQLite databases. It is very, very dumb. The original justification was that loading 500.000 locations codes (during regionalized LCA) was much faster in one file than a big database query, and JSON allowed configurations to be edited without having to know how to use a relational database. These reasons are inadequate.

Specific tasks:

* D1 Migrate all data storage in `bw2data` to SQLite databases.

Nice-to-have:

* D2 Use the SQLite text search instead of a separate Whoosh search index.

## eILCD as standard interface between `bw_data` and `bw_io`

The current interface between `bw2data` and `bw2io` is inadequate - it does not include a lot of important metadata, it grew organically without clear design or vision, it doesn't not distinguish between inventory and impact assessment, and it barely specified and therefore impossible to implement by outside collaborators.

Specific tasks:

* E1 `bw_io` needs to to support the Brightway Common Database standard
* E2 Python decorator to use old-style `bw_io` strategies without converting internal logic to ILCD data standard

Nice-to-have:

* E3 `bw_io` strategies rewritten to use the ported ILCD data standard internally
* E4 Code audit of `bw_io` for test coverage and strategy obsolescence

## Infrastructure

### [Documentation](https://github.com/brightway-lca/brightway2/issues/36)

Documentation needs to be reworked and improved. A more decoupled organization of the Brightway 3 libraries should also make (new) contributions easier.

Specific tasks:

* F1 Develop new Sphinx template with a [three column layout](https://github.com/Depart-de-Sentier/Prizes/issues/2#issuecomment-1077682124)
* F2 Reorganize documentation following the [Diataxis framework](https://diataxis.fr/) for technical documentation
* F3 Each notebook (where possible) should link to a *try.brightway.dev* container
* F4 Develop, document, and test contribution guidelines and coding styles, and apply to all libraries

### [Homogeneous build, test and deploy metrics](https://github.com/brightway-lca/enhancement-proposals/issues/3)

The repositories of code for Brightway 3 core libraries will have the same building, deploying and testing infrastructure and badges on the README.

Specific tasks:

* G1 Make `cookiecutter` template that satisfies the required attributes
* G2 Document use of this template, both for new library creation and for updating libraries
* G3 Create example project from the example template
* G4 Have regular checks to ensure that all Brightway libraries work correctly as dependent libraries evolve

## Governance

An important part of Brightway maturing is a formal decision making process for making changes to and prioritizing development in Brightway. To that end, we will:

* H1 Create a structured process for making breaking changes or adding major features to Brightway (see the [proposal template](https://github.com/brightway-lca/enhancement-proposals/blob/main/proposals/0001-bep-template.md)), based on Python enhancement proposals.
* H2 Create a Steering Committee which will vote on BEPs
* H3 Create a Brightway Users Group as a formal forum to provide feedback from Brightway users and key stakeholders

[Départ de Sentier](https://www.d-d-s.ch/) (DdS) will manage the Steering Committee and Users Group. Managing the Brightway project, and organizing the Brightcon conference, are two core activities of DdS.

## Dependency graph

Not all tasks can be done simultaneously. The follow chart shows the needed order of operations:

```mermaid
  flowchart TD

  subgraph bw_calc
    A1 --> A2
    A2 --> A6
    A2 --> A3
    A4 --> A5
  end

  subgraph common_api
    B1 --> B2
    B2 --> B4
    B3
    B2 --> B5
    B5 --> B6
  end

  B5 --> A5

  subgraph projects
    C1 --> C2
    C2 --> C3
  end

  B5 --> projects

  subgraph bw_data
    D1 --> D2
  end

  common_api --> bw_data
  B3 --> D2

  subgraph bw_io
    E1 --> E2
    E1 --> E3
    E4
  end

  subgraph docs
    F1
    F2 --> F3
    F4
  end

  subgraph infrastructure
    G1 --> G2
    G2 -> G3
    G4
  end

  infrastructure --> bw_calc
  infrastructure --> common_api
  infrastructure --> bw_data
  infrastructure --> bw_io
```

