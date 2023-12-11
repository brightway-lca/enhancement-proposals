# BEP-0005 Brightway Dependency Management Strategy

| | |
| - | - |
| Number | 5 |
| Title | Brightway Dependency Management Strategy |
| Status | Draft |
| Type | Guidelines |
| Proposed By | [Michael Weinold](mailto:dev@weinold.ch) |
| Created | 2023-08-01 |
| Last updated | 2023-12-13 |
| Version | 1 |

## Abstract

New dependencies for Brightway should either be written in pure Python, or be compatible with WebAssembly (ie. compiled by [Pyodide](https://pyodide.org/en/stable/usage/packages-in-pyodide.html) or [emscripten-forge](https://github.com/jtpio/emscripten-forge-recipes)). This will ensure the continued compatibility of Brightway with WebAssembly.

## Motivation

As the Python/WebAssembly ecosystem (eg. [Pyodide](https://pyodide.org/en/stable/), [JupyterLite](https://jupyterlite.readthedocs.io/en/stable/), [WASM as a 1st class Python platform](https://discuss.python.org/t/make-wasm-a-1st-class-platform-in-the-python-ecosystem/21798), etc.) grows, "Python in the Browser" will likely become ubiquitous. This will offer new opportunities for using Brightway in a teaching context. Time/Resource-intensive maintenance of JupyterHub servers can be replaced by a simple web server hosting a static website. Platform-dependent installation issues will be a thing of the past. However, this will require a new approach to dependency management. While the majority of Brightway dependencies are written in pure Python, some are using ["C-extensions"](https://docs.python.org/3/extending/extending.html). In order to ensure the compatibility of Brighway with WebAssembly, all future dependencies shall be written in pure Python.

## Proposal

Detailed description of the proposed idea of solution. Normative statements should follow [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt). Must include the following subsections (some of which are optional); additional sections may be added:

For any new dependency, the following determination shall be made:

1. Is the dependency written in pure Python?
2. If not, is the dependency compatible with WebAssembly?

If the answer to both questions is "no", the dependency shall not be introduced.
Compatibility with WebAssembly can be determined examining the list of non-Pure-Python packages already compiled by [Pyodide](https://pyodide.org/en/stable/usage/packages-in-pyodide.html) or [emscripten-forge](https://github.com/jtpio/emscripten-forge-recipes).

### Rationale

The rationale is clear: Brightway will remain compatible with WebAssembly. "Cleaning" the dependency tree of the `bw25` versions of the major Brightway packages has been a time-consuming process (cf. https://github.com/brightway-lca/brightway-live/discussions/21). Ensuring that all future dependencies are WebAssembly-compatible will save time and resources.

### Pros and Cons

Pros: Brightway will remain compatible with WebAssembly. 

Cons: A potential drawback are the minor performance penalties that would be incurred by using a dependency written in pure Python instead of a C-extension. However, many relevant high-performance packages with C-extensions have already been compiled to WebAssembly (both for [Pyodide](https://pyodide.org/en/stable/usage/packages-in-pyodide.html) and for [emscripten-forge](https://github.com/jtpio/emscripten-forge-recipes)).

### Alternatives

Not introduce a dependency management strategy. The compatibility of Brightway with WebAssembly will not be guaranteed. 

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

- Version 1 (this version)