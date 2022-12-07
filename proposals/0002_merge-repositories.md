# BEP-0002 Merge Brightway Repositories

| | |
| - | - |
| Number | 2 |
| Title | Merge Brightway Repositories |
| Status | Draft |
| Type | Software features |
| Proposed By | [Benjamin W. Portner](mailto:benjamin.portner@bauhaus-luftfahrt.net) |
| Created | 2022-07-19 |
| Last updated | 2022-07-19 |
| Version | 0.0.1 |

## Abstract

Brightway's source code is currently spread across six Github repositories (brightway, bw-io, bw-data, bw-calc, bw-analyzer, matrix utils). This leads to several problems for both users and developers of Brightway: Users do not know where to open new issues. Users do not know from which package to import the functions they need. Developers need more time to sync multiple repos. It is not guaranteed that the latest version of repo x is compatible with the latest version of repo y. It is harder to track bugs across multiple packages. New features can need PRs in multiple repositories, thus needing more time and increasing the risk of incompatibilities. And so on. All repositories should thus be merged into one.

## Motivation

See abstract.

## Proposal

Keep the `brightway` repository and move the source code of `bw-io`, `bw-data`, `bw-calc`, `bw-analyzer`, and `matrix utils` into subfolders of `brightway`. Keep `bw-io`, `bw-data`, `bw-calc`, `bw-analyzer`, and `matrix utils` on Github for now, but mark them as legacy. 

### Rationale

See abstract.

### Pros and Cons

Contra separate repositories:
- Users do not know where to open new issues
- Users do not know from which package to import the functions they need
- Developers need more time to sync multiple repos
- It is not guaranteed that the latest version of repo x is compatible with the latest version of repo y, possibly preventing developer participation
- It is harder to track bugs across multiple packages, increasing developing times
- New features can need PRs in multiple repositories, increasing developing times

Pro merging repositories:
- Tests and test fixtures can be re-used across repositories

Contra merging (pro separate repositories):
- Enlighten me!

### Alternatives

TBD

### Open Issues

TBD

### Non-Goals

- Make brightway harder to use
- Make brightway harder to develop

### Test plan and results

Implement the change. Collect user and developer feedback. Revert change if necessary.

## BEP metadata

See beginning of document.

## Discussion

* [BEP-0002 Discussion on GitHub](https://github.com/brightway-lca/enhancement-proposals/discussions/23)
  
Previously proposed (unfortunately not discussed) in:
* https://brightway.groups.io/g/development/message/61

## Previous Versions

None so far.

## Copyright

To the extent possible under law, Benjamin W. Portner has waived all copyright and related or neighboring rights to Brightway Enhancement Proposal 2: Merge Brightway Repositories. This work is published from: Germany.
