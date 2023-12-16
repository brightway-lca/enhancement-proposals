# BEP-0004 Changelog Files for Releases

| | |
| - | - |
| Number | 4 |
| Title | Changelogs for Brightway Packages |
| Status | Accepted |
| Type | Guidelines |
| Proposed By | [Michael Weinold](mailto:dev@weinold.ch) |
| Editor | [Tomas Navarrete Gutierrez](mailto:tomas.navarrete@list.lu) |
| Created | 2022-11-14 |
| Last updated | 2023-12-13 |
| Version | 4 |

## Abstract

In order for the new documentation (compare BEP-0003) to provide users with a single place to get information on _"what's new"_ with Brightway, every Brightway repository (including the below listed) shall include a `CHANGES.md` markdown file. The file content shall adhere to best practices laid out by the [`keep a changelog`](https://keepachangelog.com/en/1.0.0/) project and conform to [Semantic Versioning > 2.0.0](https://semver.org/).

## Motivation

[Prior to](https://web.archive.org/web/20200716020925/https://brightway.dev/) the [update of the documentation](https://github.com/brightway-lca/brightway-documentation/milestones?state=closed) in 2022/2023, there was no way for users to obtain information on feature changes and bug fixes from the documentation website. Instead, they needed to check for every package by comparing the (differently named) changelog files in the respective GitHub repositories:

| repo | changelog file URL |
| ---- | ------------------ |
| `io` | https://github.com/brightway-lca/brightway2-io/blob/master/CHANGES.md |
| `data` | https://github.com/brightway-lca/brightway2-data/blob/main/CHANGES.md |
| `calc` | https://github.com/brightway-lca/brightway2-calc/blob/master/CHANGES.md |
| `processing` | https://github.com/brightway-lca/bw_processing/blob/master/CHANGELOG.md | 
| `analyzer` | https://github.com/brightway-lca/brightway2-analyzer/blob/master/CHANGES.md |
| `speedupds` | https://github.com/brightway-lca/brightway2-speedups/blob/master/CHANGELOG.md |
| `matrix_utils` | https://github.com/brightway-lca/matrix_utils/blob/main/CHANGELOG.md |
| `regional` | https://github.com/brightway-lca/brightway2-regional/blob/master/CHANGES.md |
| `regional` | https://github.com/brightway-lca/bw_migrations/blob/master/CHANGELOG.md |

Unifying the file names, syntax and best practices will enable these changelog files to be included in the new Brightway documentation.

## Proposal

Every Brightway repository shall include a changelog file (Markdown `.md` format) named (path relative to project root): 

```
/CHANGES.md
```

The content shall adhere to the best practices laid out by the [_keep a changelog_](https://keepachangelog.com/en/1.0.0/) project:

> __Guiding Principles:__ \
Changelogs are for humans, not machines. \
There should be an entry for every single version. \
The same types of changes should be grouped. \
Versions and sections should be linkable. \
The latest version comes first. \
The release date of each version is displayed. \
Mention whether you follow Semantic Versioning.

> __Types of changes:__ \
Added for new features. \
Changed for changes in existing functionality. \
Deprecated for soon-to-be removed features. \
Removed for now removed features. \
Fixed for any bug fixes. \
Security in case of vulnerabilities.

For a style guide, compare the _keep a changelog_ [`CHANGELOG.md`](https://raw.githubusercontent.com/olivierlacan/keep-a-changelog/main/CHANGELOG.md). In the context of Brightway development, this means:  

Every changelog entry for a major release (full bump in version number) must:

1. include the version number of the corresponding release
1. include a full text description of the changes, in addition to:
2. a list of individual changes, which:
3. link to relevant GitHub issues (e.g. `#1`, `#2`)

Every changelog entry for a minor release (no full bump in version numver) must:

1. include the version number of the corresponding release
2. include a list of individual changes, which:
3. link to relevant GitHub issues (e.g. `#1`, `#2`)

In addition, the version numbers shall adhere to [Semantic Versioning](https://semver.org/):

> Given a version number MAJOR.MINOR.PATCH, increment the: \
> \
MAJOR version when you make incompatible API changes\
MINOR version when you add functionality in a backwards compatible manner\
PATCH version when you make backwards compatible bug fixes\
Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.\

### Rationale

Unless BEP-0002 is accepted, the various Brightway packages will be maintained as separate repositories. To ensure the Sphinx documentation is able to pull changelog information from these repositories, they must follow a common naming and formatting convention.

### Pros and Cons

Pros: Uniform formatting and structure across the changelog files of all Brightway packages. Improved readability, improved accountability of developers. Improved accessibility by end-users.

Cons: None

### Alternatives

Maintain status quo, include changelogs in the documentation but without a common naming and formatting convention.

### Open Issues

- [X] [brightway-documentation#13](https://github.com/brightway-lca/brightway-documentation/issues/13)

### Non-Goals

N/A

### Test plan and results

The prototype of [documentation.brightway.dev](https://documentation.brightway.dev/) already contains a [`Changelog`](https://documentation.brightway.dev/en/latest/source/5_changelog/0_index.html) sub-page. No further testing is required.

## Discussion

* [BEP-0004 Discussion on GitHub](https://github.com/brightway-lca/enhancement-proposals/discussions/26)
*  The [Gitter `documentation` channel](https://gitter.im/brightway-lca/documentation)
* The Brightway development discussion list, tagged with [#BEP0004]
* Issues in the respective repositories:
   - [brightway-lca/brightway-documentation](https://github.com/brightway-lca/brightway-documentation/issues/13)

## Previous Versions

 - [Version 1](https://github.com/brightway-lca/enhancement-proposals/blob/2d904c1e457ad589c2e2ea7d2434c7d360989a0f/proposals/0004_changelogs.md)
 - [Version 2](https://github.com/brightway-lca/enhancement-proposals/blob/662bd104ba8c83e313b966a9c5893b2e3c95376a/proposals/0004_changelogs.md)
 - [Version 3](https://github.com/brightway-lca/enhancement-proposals/blob/a3043a12d1e50f27dc7c809ca50e0dd76e909381/proposals/0004_changelogs.md)
 - Version 4 (this version)