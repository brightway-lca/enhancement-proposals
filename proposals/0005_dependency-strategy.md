# BEP-0005 Brightway Dependency Management Strategy

| | |
| - | - |
| Number | 5 |
| Title | Brightway Dependency Management Strategy |
| Status | Proposed |
| Type | Guidelines |
| Proposed By | [Michael Weinold](mailto:dev@weinold.ch) |
| Created | 2023-08-01 |
| Last updated | 2023-12-13 |
| Version | 2 |

## Abstract

New dependencies for Brightway should be either: \
Platform independent (with support for the three major plaforms [`x86_64`, `aarch64`, `wasm32`, as defined in  PEP11](https://peps.python.org/pep-0011/)), or... \
Fail gracefully only on first call (not on package import), according to the _"lazy import"_ logic defined in [PEP690](https://peps.python.org/pep-0690/). \
This will ensure that, without additional maintainer effort, Brightway will remain compatible with WebAssembly and Apple Silicon.

## Motivation

As the Python/WebAssembly ecosystem (eg. [Pyodide](https://pyodide.org/en/stable/), [JupyterLite](https://jupyterlite.readthedocs.io/en/stable/), [WASM as a 1st class Python platform](https://discuss.python.org/t/make-wasm-a-1st-class-platform-in-the-python-ecosystem/21798), etc.) grows, "Python in the Browser" will likely become ubiquitous. This will offer new opportunities for introducing new users to Brightway, or quickly setting up "beginner-level" classes in a JupyterHub-lite environment. Time/Resource-intensive maintenance of the usually required JupyterHub servers can be replaced by a simple web server hosting a static website. Platform-dependent installation issues will be a thing of the past. Similarly, the adoption of Apple Silicon will likely increase, as Apple has announced that they will transition their entire product line to Apple Silicon. Some Brightway dependencies are not yet compatible with either WebAssembly or Apple Silicon. This will require that Brightway adhere to well-established dependency best-practices of the Python ecosystem. 

## Proposal

For any new dependency, the following determination shall be made:

1. Is the dependency compatible with the three major platforms [`x86_64`, `aarch64`, `wasm32`, as defined in  PEP11](https://peps.python.org/pep-0011/)?
2. Is a platform-specific version of the dependency available for the platform(s) not supported in 1.? If so, the dependency shall be introduced as a platform-specific dependency, with the appropriate `setup.py` logic.
2. If neither 1. or 2. apply, the dependency shall fail gracefully only on first call of the related function, according to the _"lazy import"_ logic defined in [PEP690](https://peps.python.org/pep-0690/).

This will ensure that Brightway packages can still be imported, even if the dependency is not available for a specific platform.

### Rationale

Brightway will adopt a weaker version of PEP690, where lazy imports are required only for dependencies that are not compatible with all target platforms. Ensuring that all future dependencies adhere to BEP005 will allow developers to maintain compatibility with WebAssembly and Apple Silicon without additional effort.

### Pros and Cons

Pros: Brightway will remain compatible with WebAssembly and Apple Silicon without additional maintainer effort.

Cons: None

### Alternatives

Not introduce a dependency management strategy.

### Open Issues

N/A

### Non-Goals

N/A

### Test plan and results

N/A

## Discussion

- https://github.com/brightway-lca/brightway-live/issues/7
- https://github.com/brightway-lca/brightway-live/discussions/21

## Previous Versions

- Version 1 (unpublished, part of [PR#29](https://github.com/brightway-lca/enhancement-proposals/pull/29))
- Version 2 (this version)