# BEP-0004 Changelog Files for Releases

| | |
| - | - |
| Number | 4 |
| Title | Brightway (BEP) Enhancement Proposal Template |
| Status | Draft |
| Type | Guidelines |
| Proposed By | [Michael Weinold](mailto:dev@weinold.ch) |
| Editor | [Chris Mutel](mailto:cmutel@gmail.com) |
| Created | 2022-11-14 |
| Last updated | 2022-11-14 |
| Version | 1 |

## Abstract

In order for the new documentation (compare [BEP-0003](https://github.com/brightway-lca/enhancement-proposals/blob/ca80e219917ed612f74936fd7f7e60cb3ee1b2eb/proposals/0003_documentation.md)) to provide users with a single place to get information on "what's new" with Brightway, every Brightway repository (including the below listed) shall include a `CHANGELOG.rst` file. The file content shall adhere to best practives laid out by the [`keep a changelog`](https://keepachangelog.com/en/1.0.0/) project.

## Motivation

Clearly explain why the existing specifications is inadequate to address the problem that the BEP solves

| repo | changelog file URL |
| ---- | ------------------ |
| `io` | https://github.com/brightway-lca/brightway2-io/blob/master/CHANGES.md |
| `data` | https://github.com/brightway-lca/brightway2-data/blob/main/CHANGES.md |
| `calc` | https://github.com/brightway-lca/brightway2-calc/blob/master/CHANGES.md |
| `processing` | https://github.com/brightway-lca/bw_processing/blob/master/CHANGELOG.md | 
| `analyzer` | https://github.com/brightway-lca/brightway2-analyzer/blob/master/CHANGES.md |
| `matrix_utils` | https://github.com/brightway-lca/matrix_utils/blob/main/CHANGELOG.md |

## Proposal

Every Brightway repository shall include a changelog file according to the naming convention (path relative to project root): 

```
/CHANGELOG.rst
```


Detailed description of the proposed idea of solution. Normative statements should follow [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt). Must include the following subsections (some of which are optional); additional sections may be added:

The proposal does not need to be exhaustive, if the proposed standards or software are otherwise available and well documented.

### Rationale

Unless [BEP-0002](https://github.com/brightway-lca/enhancement-proposals/blob/ca80e219917ed612f74936fd7f7e60cb3ee1b2eb/proposals/0002_merge-repositories.md) is accepted, the various Brightway packages will be maintained as separate repositories. To ensure the Sphinx documentation is able to pull changelog information from these repositories, they must follow a common naming and formatting convention.

### Pros and Cons

Pros: 
Cons: None

### Alternatives

Maintain status quo, do not include changelog information in the documentation website.

### Open Issues

N/A

### Non-Goals

N/A

### Test plan and results

The XXX can be seen at XXX

## Discussion

Link to the GitHub Discussion for this BEP here. Also add a comprehensive bullet list of links to where the BEP has been discussed by the community, such as the Brightway developers mailing list, and Github pull requests and issues. For example:

* [BEP-0004 Discussion on GitHub](https://github.com/brightway-lca/enhancement-proposals/discussions/04)
* The Brightway development discussion list, tagged with [#BEP0004]

A procedure to implement/reject modifications to the BEP shall be mentioned in the proposal. Depending on the type of BEP, examples can be one or more of the following options:

* BEP result of working groups already reflect some level of consensus, and will have a history of how the specifics came to be. In this case, the author will mention that the group is the primary and preliminary place for discussing the proposal, before it is made public.
* Once the BEP is public, the authors should publicly respond to suggested changes by either accepting the changes, or providing their reasons to reject the suggested changes.
* If discussion is particularly heated, the authors may invite changes via pull request which would be discussed by the community. To avoid voting overload, this procedure should only be used in special cases.
* Alternatively, the authors or the editor may invite dissenting discussion participants to phone or in-person conferences to reach consensus on difficult issues.