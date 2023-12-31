<!-- These are examples of badges you might want to add to your README:
     please update the URLs accordingly

[![ReadTheDocs](https://readthedocs.org/projects/assorthead/badge/?version=latest)](https://assorthead.readthedocs.io/en/stable/)
[![Coveralls](https://img.shields.io/coveralls/github/<USER>/assorthead/main.svg)](https://coveralls.io/r/<USER>/assorthead)
[![Conda-Forge](https://img.shields.io/conda/vn/conda-forge/assorthead.svg)](https://anaconda.org/conda-forge/assorthead)
[![Twitter](https://img.shields.io/twitter/url/http/shields.io.svg?style=social&label=Twitter)](https://twitter.com/assorthead)
-->

[![Project generated with PyScaffold](https://img.shields.io/badge/-PyScaffold-005CA0?logo=pyscaffold)](https://pyscaffold.org/)
[![PyPI-Server](https://img.shields.io/pypi/v/assorthead.svg)](https://pypi.org/project/assorthead/)
![Unit tests](https://github.com/BiocPy/assorthead/actions/workflows/pypi-test.yml/badge.svg)

# Assorted C++ headers

## Overview

**assorthead** vendors an assortment of header-only C++ libraries for compilation of downstream packages.
This centralizes the acquisition and versioning of these libraries for a smoother development experience.
It is primarily intended for the various [**BiocPy**](https://github.com/BiocPy) packages with C++ extensions,
e.g., [**scranpy**](https://github.com/BiocPy/scranpy), [**singler**](https://github.com/BiocPy/singler).

## Quick start

Developers can install **assorthead** via the usual `pip` commands:

```shell
pip install assorthead
```

We can then add all headers to the compiler's search path, 
using the `include_dirs` argument in the `setup()` command in our `setup.py`:

```python
setup(
    use_scm_version={"version_scheme": "no-guess-dev"},
    ext_modules=[
        Extension(
            "foo.core",
            [
                "src/lib/foo.cpp",
                "src/lib/bar.cpp",
            ],
            include_dirs=[
                assorthead.includes(),
            ],
            language="c++",
            extra_compile_args=[
                "-std=c++17",
            ],
        )
    ],
)
```

Of course, this is only relevant for developers; all going well, end users should never be aware of these details.

## Available libraries

| Name | Description |
|------|-------------|
| [**byteme**](https://github.com/LTLA/byteme) | Lightweight file readers/writers |
| [**aarand**](https://github.com/LTLA/aarand) | Random distribution functions |
| [**powerit**](https://github.com/LTLA/powerit) | Power iterations |
| [**kmeans**](https://github.com/LTLA/CppKmeans) | Hartigan-Wong or Lloyd k-means |
| [**Annoy**](https://github.com/spotify/Annoy) | Approximate nearest neighbor search |
| [**hnswlib**](https://github.com/nmslib/hnswlib) | Approximate nearest neighbor search |
| [**knncolle**](https://github.com/LTLA/knncolle) | Common interface to neighbor search algorithms |
| [**tatami**](https://github.com/tatami-inc/tatami) | Interface for matrix representations |
| [**qdtsne**](https://github.com/LTLA/qdtsne) | Visualiation with t-SNE |
| [**umappp**](https://github.com/LTLA/umappp) | Visualization with UMAP |
| [**Eigen**](https://gitlab.com/libeigen/eigen) | Matrix operations and linear algebra | 
| [**irlba**](https://github.com/LTLA/CppIrlba) | Approximate SVD via IRLBA |
| [**WeightedLowess**](https://github.com/LTLA/CppWeightedLowess) | Trend fitting via weighted LOWESS |
| [**mnncorrect**](https://github.com/LTLA/CppMnnCorrect) | Batch correction with MNNs |

The exact versions of each library can be found in [`extern/fetch.sh`](extern/fetch.sh).

<!-- pyscaffold-notes -->

## Note

This project has been set up using PyScaffold 4.5. For details and usage
information on PyScaffold see https://pyscaffold.org/.
