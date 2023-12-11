# BEP-0003 Brightway Documentation Strategy

| | |
| - | - |
| Number | 3 |
| Title | Brightway Documentation |
| Status | Proposed |
| Type | Guidelines |
| Proposed By | [Michael Weinold](mailto:dev@weinold.ch), [Chris Mutel](mailto:cmutel@gmail.com) |
| Editor | [Tomas Navarrete Gutierrez](mailto:tomas.navarrete@list.lu) |
| Created | 2022-10-09 |
| Last updated | 2023-01-09 |
| Version | 4 |

## Abstract

As the functionality and user base of Brightway continues to grow, the documentation must grow too. As part of the [Brightway Strategic Development Plan](https://github.com/brightway-lca/enhancement-proposals/blob/main/Brightway%20strategic%20development%20plan.md#documentation) (F1-F4), the documentation should be made compliant with the [Diataxis framework](https://diataxis.fr/) for technical documentation.

## Motivation

[Prior to](https://web.archive.org/web/20200716020925/https://brightway.dev/) the [update of the documentation](https://github.com/brightway-lca/brightway-documentation/milestones?state=closed) in 2022/2023, a Google search for "Brightway documentation" returned:

| website |
| ------- | 
| https://2.docs.brightway.dev/ |
| https://brightway.dev/ (redirects to the above) |
| https://brightway-docs.readthedocs.io/ |

The primary documentation previously at https://2.docs.brightway.dev/ was difficult to navigate for first-time users. It does not differentiate clearly between different user needs and offers no interactivity. In addition, various notebooks written as part of training events and seminars are collected separately at [brightway-lca/brightway2](https://github.com/brightway-lca/brightway2/tree/master/notebooks) and at [brightway-lca/from-the-ground-up](https://github.com/brightway-lca/from-the-ground-up). Some are outdated (Jupyter Notebook version) and can no longer be viewed in GitHub. An alltogether confusing state of affairs!

A solution has been proposed by @tngTUDOR in the form of the Diataxis Framework. This framework was created and developed by Daniele Procida during his tenure at Divio. It formalizes different types of technical documentation according to the different needs of users. It is widely adopted in software development (e.g. at [Canonical, Cloudflare, Google, etc.](https://diataxis.fr/adoption/)).

|    | serve our study | serve our work |
| -: | :-------------: | :------------: |
practical steps | __Tutorials__ <br/> _learning-oriented_ | __How-To Guides__ <br/> _task-oriented_ |
theoretical knowledge | __Explanation__ <br/> _understanding-oriented_ | __Reference__ <br/> _information-oriented_ |

Table 1: The [Diataxis framework](https://diataxis.fr/) 

The framework makes an [important distinction based on the needs of the user](https://diataxis.fr/tutorials-how-to/): The purpose of a _tutorial_ is to provide a successful _learning experience_. The purpose of a _how-to guide_ is to to help the user _accomplish a task_.

## Proposal

All code added to the Brightway code base shall include docstrings conforming to the [Numpy Style Guide](https://numpydoc.readthedocs.io/en/latest/format.html). Existing code that does not conform to this standard shall be considered legacy code and shall be refactored. New code that does not conform to this standard shall not be merged into the Brightway code base.

Based on the Diataxis framework, all Brightway documentation shall be structured as follows:

|    | serve our study | serve our work |
| -: | :-------------: | :------------: |
practical steps | __Tutorials (=E-Book)__ <br/> Pages at <br/>  [`learn.brightway.dev`](https://github.com/brightway-lca/brightway-training) | __How-To Guides__ <br/> "Gallery" at <br/> [`docs.brightway.dev`](https://github.com/brightway-lca/brightway-documentation) |
theoretical knowledge | __Explanation__ <br/> "LCA" at <br/> [`docs.brightway.dev`](https://github.com/brightway-lca/brightway-documentation)| __Reference__ <br/> "API Reference" at <br/>  [`docs.brightway.dev`](https://github.com/brightway-lca/brightway-documentation) |

Table 2: The [Brightway](https://github.com/brightway-lca) implementation of the [Diataxis framework](https://diataxis.fr/)

##### Reference

This shall contain the API reference for the various Brightway modules (`bw_agg`, `bw_calc`, `bw_data`, ...). This is compiled automatically from the function docstrings by the [Sphinx package](https://www.sphinx-doc.org/en/master/).

##### Explanation

This shall include the [mathematical formalism of life-cycle assessment](https://doi.org/10.1007/978-94-015-9900-9), some theory of matrix multiplication, etc. The exact contents are to be discussed based on the __"Scope of the Documentation"__ section.

##### Tutorials

This shall include the growing number of high-quality interactive Jupyter Notebooks already available at [`brightway-lca/brightway2/notebooks`](https://github.com/brightway-lca/brightway2/tree/master/notebooks), as well as some of the notebooks [collected as part of the 2022 Brightcon Hackathon](https://github.com/brightway-lca/brightway-training/blob/master/organization/curation/brightway_tutorial_list.xlsx).

##### How-To Guides ("Example Gallery")

This shall contain self-contained examples of Brightway code. Examples shall be collected in the [`example-gallery`](https://github.com/brightway-lca/brightway-examples) repository. They are integrated into the documentation website using a git submodule and the [`myst-nb`](https://myst-nb.readthedocs.io/en/latest/) package.

### Rationale

The `pydata-sphinx-theme` and the `jupyter-book` templates in combination with readthedocs.org are free and open source, future-proof options of hosting documentation.

### Pros and Cons

Pros: An established future-proof standard of documenting code that will result in lower entry barriers for users with little experience in Python.

Cons: Developers will need to write documentation (gasp!).

#### Cons

N/A

### Alternatives

N/A

### Open Issues

Compare the open issues in the respective repositories:

 - [brightway-lca/brightway-documentation](https://github.com/brightway-lca/brightway-documentation)
 - [brightway-lca/brightway-book](https://github.com/brightway-lca/brightway-book)
 - [brightway-lca/brightway-live](https://github.com/brightway-lca/brightway-live)

### Non-Goals

N/A

### Test plan and results

Prototypes of [docs.brightway.dev](https://docs.brightway.dev/) and [learn.brightway.dev](https://learn.brightway.dev/) were developed as part of the [Brightcon 2022](http://web.archive.org/web/20220928071701/https://2022.brightcon.link/) Hackathon. The prototype of [live.brightway.dev](https://live.brightway.dev/) was developed as part of the [Brightcon 2023](https://web.archive.org/web/20230918043912/https://2023.brightcon.link/) hackathon.

The readthedocs.org traffic analysis confirms the success of the new documentation (data as per December 2023):

| Site | Daily Page Views |
| ---- | ---------------- |
| [docs.brightway.dev](https://docs.brightway.dev/) | 500-600 |
| [learn.brightway.dev](https://learn.brightway.dev/) | ~100 |
| [live.brightway.dev](https://live.brightway.dev/) | ~50 |

## Discussion

 - [BEP-0003 Discussion on GitHub](https://github.com/brightway-lca/enhancement-proposals/discussions/21)
 - The [Gitter `documentation` channel](https://gitter.im/brightway-lca/documentation)
 - [F1-F4 of the Strategic Development Plan](https://github.com/brightway-lca/enhancement-proposals/blob/main/Brightway%20strategic%20development%20plan.md#documentation)
 - The [Brightcon 2022](http://web.archive.org/web/20220928071701/https://2022.brightcon.link/) Hackathon, with results of the brainstorming sessions documented in [#10 Improve Brightway Documentation](https://github.com/brightway-lca/hackathons/issues/10)
 - Issues in the respective repositories:
   - [brightway-lca/brightway-training](https://github.com/brightway-lca/brightway-training)
   - [brightway-lca/brightway-documentation](https://github.com/brightway-lca/brightway-documentation)

Compare also the [Development Meeting Minutes](https://github.com/brightway-lca/brightway-documentation/discussions/31) in the `brightway-documentation` repo.

## Previous Versions

- [Version 1](https://github.com/brightway-lca/enhancement-proposals/blob/ca80e219917ed612f74936fd7f7e60cb3ee1b2eb/proposals/0003_documentation.md)
- [Version 2 (incorrectly labeled "4")](https://github.com/brightway-lca/enhancement-proposals/blob/a3043a12d1e50f27dc7c809ca50e0dd76e909381/proposals/0003_documentation.md)
- [Version 3 (incorrectly labeled "4")](https://github.com/brightway-lca/enhancement-proposals/blob/0fd4f17c74a679ea2a966214fc95d6b2a7bb05f3/proposals/0003_documentation.md)
- Version 4 (this version)