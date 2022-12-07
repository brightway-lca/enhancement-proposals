# BEP-0003

| | |
| - | - |
| Number | 3 |
| Title | Brightway Documentation |
| Status | Draft |
| Type | Guidelines |
| Proposed By | [Michael Weinold](mailto:dev@weinold.ch), [Chris Mutel](mailto:cmutel@gmail.com) |
| Created | 2022-10-09 |
| Last updated | 2022-10-09 |
| Version | 1 |

## Abstract

As the functionality and user base of Brightway continues to grow, the documentation must grow too. As part of the [Brightway Strategic Development Plan](https://github.com/brightway-lca/enhancement-proposals/blob/main/Brightway%20strategic%20development%20plan.md#documentation) (F1-F4), the documentation should be made compliant with the [Diataxis framework](https://diataxis.fr/) for technical documentation. It should be split up into a user-focused interactive website containing tutorials and into a more developer-focused website containing the API reference as well as a gallery of how-to guides and some theoretical information on life-cycle assessment.

## Motivation

Currently (prior to the 2022 Brightcon Hackathon), a Google search for "Brightway documentation" returnes:
| website |
| ------- | 
| https://2.docs.brightway.dev/ |
| https://brightway.dev/ (redirects to the above) |
| https://brightway-docs.readthedocs.io/ |

Various notebooks written as part of training events and seminars are further collected at https://github.com/brightway-lca/brightway2/tree/master/notebooks. Some are outdated (Jupyter Notebook version) and can no longer be viewed in GitHub.

The primary documentation at https://2.docs.brightway.dev/ is difficult to navigate for first-time users. It does not differentiate clearly between different user needs and offers not interactivity.

## Proposal

#### The Diataxis Framework

The Diataxis framework was created and developed by Daniele Procida during his tenure at Divio. It formalizes different types of technical documentation according to the different needs of users. It is widely adopted in software development (e.g. at [Canonical, Cloudflare, Google, etc.](https://diataxis.fr/adoption/)).

|    | serve our study | serve our work |
| -: | :-------------: | :------------: |
practical steps | __Tutorials__ <br/> _learning-oriented_ | __How-To Guides__ <br/> _task-oriented_ |
theoretical knowledge | __Explanation__ <br/> _understanding-oriented_ | __Reference__ <br/> _information-oriented_ |

Table 1: The [Diataxis framework](https://diataxis.fr/) 

##### Tutorials vs How-To Guides

The framework distinguishes based on the needs of the user: The purpose of a _tutorial_ is to provide a successful _learning experience_. The purpose of a _how-to guide_ is to to help the user _accomplish a task_.

🌐 [Diataxis documentation: _Tutorials_ vs _How-To Guides_ ](https://diataxis.fr/tutorials-how-to/)



#### The Brightway Documentation Strategy

The documentation for Brightway shall be structured to conform to the Diataxis framework:

|    | serve our study | serve our work |
| -: | :-------------: | :------------: |
practical steps | __Tutorials (=Training)__ <br/> All tutorials at <br/>  [`training.brightway.dev`](https://github.com/brightway-lca/brightway-training) | __How-To Guides__ <br/> "Gallery" at <br/> [`documentation.brightway.dev`](https://github.com/brightway-lca/brightway-documentation) |
theoretical knowledge | __Explanation__ <br/> "LCA" at <br/> [`documentation.brightway.dev`](https://github.com/brightway-lca/brightway-documentation)| __Reference__ <br/> "API Reference" at <br/>  [`documentation.brightway.dev`](https://github.com/brightway-lca/brightway-documentation) |

Table 2: The [Brightway](https://github.com/brightway-lca) implementation of the [Diataxis framework](https://diataxis.fr/)

##### Reference

This shall contain the API reference for the various Brightway modules (`bw_agg`, `bw_calc`, `bw_data`, ...). This is compiled automatically from the function docstrings by the [Sphinx package](https://www.sphinx-doc.org/en/master/).

##### Explanation

This shall include the [mathematical formalism of life-cycle assessment](https://doi.org/10.1007/978-94-015-9900-9), some theory of matrix multiplication, etc. The exact contents are to be discussed based on the __"Scope of the Documentation"__ section.

##### Tutorials

This shall include the growing number of high-quality interactive Jupyter Notebooks already available at [`brightway-lca/brightway2/notebooks`](https://github.com/brightway-lca/brightway2/tree/master/notebooks), as well as some of the notebooks [collected as part of the 2022 Brightcon Hackathon](https://github.com/brightway-lca/brightway-training/blob/master/organization/curation/brightway_tutorial_list.xlsx).

##### How-To Guides

This shall contain self-contained examples of Brightway code. This is supported by the "Gallery" functionality of the [pydata Sphinx template](https://pydata-sphinx-theme.readthedocs.io/en/stable/), as [`implemented by pvlib`](https://pvlib-python.readthedocs.io/en/stable/gallery/index.html).

#### Contributing to the Documentation

##### Contributing to `documentation.brightway.dev`

Contributors familiar with [Sphinx](https://www.sphinx-doc.org/en/master/), shall fork the [brightway-lca/brightway-documentation](https://github.com/brightway-lca/brightway-documentation) repository, add their contributions and create a pull request.

Otherwise, contributors shall open a discussion item in the respective repository.

##### Contributing to `training.brightway.dev`

Contributors familiar with [Jupyter Book](https://jupyterbook.org/en/stable/intro.html), shall fork the [brightway-lca/brightway-training](https://github.com/brightway-lca/brightway-training), add their contributions and create a pull request.

Otherwise, contributors shall open a discussion item in the respective repository.

### Rationale

The pydata Sphinx template in combination with readthedocs.org and the Jupyter Book template in combintaion with GitHub pages are free and open source, future-proof options of hosting documentation. 

### Pros and Cons

#### Pros

 - Future proof established standard of documenting code
 - Lower entry barriers for users with little experience in Python

#### Cons

- ..?

### Alternatives

Expand the current documentation and simply link to a directory containing Jupyter notebooks. Keep the current separation between "API Reference" and "Introduction and key Concepts (etc.)", instead of adopting the [four Diataxis categories](https://diataxis.fr/_images/diataxis.png).

### Open Issues

Compare the open issues in the respective repositories:
 - [brightway-lca/brightway-training](https://github.com/brightway-lca/brightway-training)
 - [brightway-lca/brightway-documentation](https://github.com/brightway-lca/brightway-documentation)

### Non-Goals

N/A

### Test plan and results

Prototypes of [documentation.brightway.dev](https://documentation.brightway.dev/) and [training.brightway.dev](https://training.brightway.dev/) were developed as part of the [Brightcon 2022](http://web.archive.org/web/20220928071701/https://2022.brightcon.link/) Hackathon. 

Work on the prototypes will continue until they are deemed ready for review by the BEP authors. The goal is to reach a level of completeness comparable to that of the [`pvlib` documentation](https://pvlib-python.readthedocs.io).


## Discussion

 - [BEP-0003 Discussion on GitHub](https://github.com/brightway-lca/enhancement-proposals/discussions/21)
 - The [Gitter `documentation` channel](https://gitter.im/brightway-lca/documentation)
 - [F1-F4 of the Strategic Development Plan](https://github.com/brightway-lca/enhancement-proposals/blob/main/Brightway%20strategic%20development%20plan.md#documentation)
 - The [Brightcon 2022](http://web.archive.org/web/20220928071701/https://2022.brightcon.link/) Hackathon, with results of the brainstorming sessions documented in [#10 Improve Brightway Documentation](https://github.com/brightway-lca/hackathons/issues/10)
 - Issues in the respective repositories:
   - [brightway-lca/brightway-training](https://github.com/brightway-lca/brightway-training)
   - [brightway-lca/brightway-documentation](https://github.com/brightway-lca/brightway-documentation)


## Previous Versions

N/A
