Canonical source for [classifiers][1] on [PyPI][2].

Classifiers [categorize projects][3] per [PEP 301][4]. Use this package to
validate classifiers in packages for PyPI upload or download.

## Usage

To install [from PyPI][5]:

```
$ pip install trove-classifiers
```

This package can be invoked as a module to print a list of classifiers:

```
$ python -m trove_classifiers | grep -Ei pyramid
Framework :: Pyramid
```

In addition, this package's API is two importable objects:

### Classifiers (`trove_classifiers.classifiers`)
A `set` containing classifiers (as strings). Useful for determining membership.

Example - determine if a classifier is valid:

```python
>>> from trove_classifiers import classifiers
>>> 'License :: OSI Approved' in classifiers
True
>>> 'Fuzzy :: Wuzzy :: Was :: A :: Bear' in classifiers
False
>>>
```

### Deprecated classifiers (`trove_classifiers.deprecated_classifiers`)
A `dict`, mapping a deprecated classifier (string) to a list of classifiers
which replaces it (strings).

Example - determine if a classifier is deprecated:

```python
>>> from trove_classifiers import deprecated_classifiers
>>> 'License :: OSI Approved' in deprecated_classifiers
False
>>> 'Natural Language :: Ukranian' in deprecated_classifiers
True
>>> deprecated_classifiers["Natural Language :: Ukranian"]
['Natural Language :: Ukrainian']
```

[1]: https://pypi.org/classifiers/
[2]: https://pypi.org
[3]: https://packaging.python.org/specifications/core-metadata/#classifier-multiple-use
[4]: https://www.python.org/dev/peps/pep-0301/
[5]: https://pypi.org/project/trove-classifiers/
