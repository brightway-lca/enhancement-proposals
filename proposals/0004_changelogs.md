# BEP-0004 Changelog Files for Releases

| | |
| - | - |
| Number | 4 |
| Title | Changelogs for Brightway Packages |
| Status | Draft |
| Type | Guidelines |
| Proposed By | [Michael Weinold](mailto:dev@weinold.ch) |
| Editor | [Tomas Navarrete Gutierrez](mailto:) |
| Created | 2022-11-14 |
| Last updated | 2022-11-28 |
| Version | 2 |

## Abstract

In order for the new documentation (compare [BEP-0003](https://github.com/brightway-lca/enhancement-proposals/blob/ca80e219917ed612f74936fd7f7e60cb3ee1b2eb/proposals/0003_documentation.md)) to provide users with a single place to get information on "what's new" with Brightway, every Brightway repository (including the below listed) shall include a `CHANGELOG.md` markdown file. The file content shall adhere to best practives laid out by the [`keep a changelog`](https://keepachangelog.com/en/1.0.0/) project.

## Motivation

Clearly explain why the existing specifications is inadequate to address the problem that the BEP solves

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


## Proposal

Every Brightway repository shall include a changelog file (Markdown format) named according to the convention (path relative to project root): 

```
/CHANGELOG.md
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

### Rationale

Unless [BEP-0002](https://github.com/brightway-lca/enhancement-proposals/blob/ca80e219917ed612f74936fd7f7e60cb3ee1b2eb/proposals/0002_merge-repositories.md) is accepted, the various Brightway packages will be maintained as separate repositories. To ensure the Sphinx documentation is able to pull changelog information from these repositories, they must follow a common naming and formatting convention.

### Pros and Cons

Pros: Uniform formatting and structure across the changelog files of all Brightway packages. Improved readability, improved accountability of developers. Improved accessibility by end-users. \
Cons: None

### Alternatives

Maintain status quo, do not include changelog information in the documentation website.

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

 - Version 1 (unpublished, compare PR)