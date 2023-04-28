# pybloomer

[pybloomer](https://github.com/masroore/pybloomer) is a Python 3 compatible fork of [pybloomfiltermmap](https://github.com/axiak/pybloomfiltermmap) by [@axiak](https://github.com/axiak).

The goal of `pybloomer` is simple: to provide a fast, simple, scalable, correct library for Bloom filters in Python.

[![Documentation Status](https://readthedocs.org/projects/pybloomer/badge/?version=latest)](https://pybloomer.readthedocs.io/en/latest/?badge=latest)
[![PyPI](https://img.shields.io/pypi/v/pybloomer.svg)](https://pypi.python.org/pypi/pybloomer)
[![PyPI](https://img.shields.io/pypi/dw/pybloomer.svg)](https://pypi.python.org/pypi/pybloomer)
[![PyPI](https://img.shields.io/pypi/pyversions/pybloomer.svg)](https://pypi.python.org/pypi/pybloomer)


## Why pybloomer?

There are a couple reasons to use this module:

* It natively uses [mmaped files](http://en.wikipedia.org/wiki/Mmap).
* It is fast (see [benchmarks](http://axiak.github.io/pybloomfiltermmap/#benchmarks)).
* It natively does the set things you want a Bloom filter to do.


## Quickstart

After you install, the interface to use is a cross between a file
interface and an ste interface. As an example:
```python
    >>> import pybloomer
    >>> fruit = pybloomer.BloomFilter(100000, 0.1, '/tmp/words.bloom')
    >>> fruit.update(('apple', 'pear', 'orange', 'apple'))
    >>> len(fruit)
    3
    >>> 'mike' in fruit
    False
    >>> 'apple' in fruit
    True
```

To create an in-memory filter, simply omit the file location:
```python
    >>> cakes = pybloomer.BloomFilter(10000, 0.1)
```
*Caveat*: it is currently not possible to persist this filter later.


## Docs

Current docs are available at [pybloomer.rtfd.io](https://pybloomer.readthedocs.io/en/latest).


## Install

To install:

```shell
    $ pip install pybloomer
```

and you should be set.

## Contributions and development

Suggestions, bug reports, and / or patches are welcome!

When contributing, you should set up an appropriate Python 3 environment and install the dependencies listed in `requirements-dev.txt`.
Package installation depends on a generated `pybloomer.c` file, which requires Cython module to be in your current environment.


## Maintainers

* [Dr. Masroor Ehsan](https://github.com/masroore)

## License

See the LICENSE file. It's under the MIT License.