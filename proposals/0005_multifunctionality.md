# BEP-0004 Support for multifunctional processes

| | |
| - | - |
| Number | 5 |
| Title | Support for multifunctional processes |
| Status | Proposed |
| Type | Guidelines |
| Proposed By | [Chris Mutel](mailto:cmutel@gmail.com) |
| Editor | [Tomas Navarrete Gutierrez](mailto:tomas.navarrete@list.lu) |
| Created | 2024-05-08 |
| Last updated | 2024-05-08 |
| Version | 1 |

## Abstract

A new process type "multifunctional" is introduced. Multifunctional processes are kept as multifunctional in the database, and are only turned into single-output unit processes when processed into datapackages. This approach allows for multiple allocation strategies to be applied and stored as numpy arrays.

A new library `bw_multifunctional` will implement this functionality. `bw2data` will be modified to emit a [Blinker signal](https://blinker.readthedocs.io/en/stable/), and `bw_multifunctional` will create a new group  in the same datapackage (the default allocation strategy), and optionally a new array datapackage with the complete set of allocation possibilities. The configuration options controlling this behaviour will be stored per database.

## Motivation

Multifunctional processes normally produce non-square technosphere matrices, as the number of products if higher than the number of processes. In order to create square technosphere matrices and solve the inventory linear algebra problem, strategies such as substitution or allocation must be applied.

## Proposal

### Rationale

### Pros and Cons

### Alternatives

### Open Issues

### Non-Goals

### Test plan and results

## Discussion

* [BEP-0005 Discussion on GitHub](https://github.com/brightway-lca/enhancement-proposals/discussions/foo)
* The Brightway development discussion list, tagged with [#BEP0005](example.com)

## Previous Versions

None
