
| |version| |downloads| |versions| |impls| |wheel| |coverage|

.. |version| image:: http://img.shields.io/pypi/v/chainmap.svg?style=flat
    :alt: PyPI Package latest release
    :target: https://pypi.python.org/pypi/chainmap

.. |downloads| image:: http://img.shields.io/pypi/dm/chainmap.svg?style=flat
    :alt: PyPI Package monthly downloads
    :target: https://pypi.python.org/pypi/chainmap

.. |versions| image:: https://img.shields.io/pypi/pyversions/chainmap.svg
    :alt: Supported versions
    :target: https://pypi.python.org/pypi/chainmap

.. |impls| image:: https://img.shields.io/pypi/implementation/chainmap.svg
    :alt: Supported implementations
    :target: https://pypi.python.org/pypi/chainmap

.. |wheel| image:: https://img.shields.io/pypi/wheel/chainmap.svg
    :alt: Wheel packaging support
    :target: https://pypi.python.org/pypi/chainmap

.. |coverage| image:: https://img.shields.io/badge/test_coverage-100%25-6600CC.svg
    :alt: Test line coverage
    :target: https://pypi.python.org/pypi/chainmap


This module is a `polyfill <https://en.wikipedia.org/wiki/Polyfill>`_,
implementing ``ChainMap`` for reasonably-recent versions of Python that do not
have ``collections.ChainMap``--namely, Python 2.6, Python 3.2, and PyPy3
releases based on Python 3.2. (It will also work as expected on Python 2.7,
PyPy, and Python 3.3+, but it is not strictly needed there since those verions'
``collections`` modules contains good ``ChainMap`` implementations.)

The code for this package is closely derived from the Python 3.5 source code,
(especially the ``collections`` and ``reprlib`` modules). Several changes have
been made to ensure Python 2.6 compatibility, and tests and packaging have been
added.

Typical usage::

    from chainmap import ChainMap

If you prefer to preferentially import from the Python standard library when
``ChainMap`` is available there::

    try:
        from collections import ChainMap
    except ImportError:
        from chainmap import ChainMap

Please see `the standard documentation <https://docs.python.org/3/library/collections.html#collections.ChainMap>`_
for details on how to use ``ChainMap``.

If you're not sure *why* someone would use a ``ChainMap``, they are useful for
managing "nested" contexts and "overlays." See e.g. my `options
<https://pypi.python.org/pypi/options>`_, `quoter
<https://pypi.python.org/pypi/quoter>`_, and `say
<https://pypi.python.org/pypi/say>`_ packages, which use them extensively for
flexible option handling. You can find similar uses in the `Context class
<https://docs.djangoproject.com/en/1.8/ref/templates/api/#django.template.Context>`_
of Django's template engine.

Notes
=====

* Automated multi-version testing managed with
  `pytest <http://pypi.python.org/pypi/pytest>`_,
  `pytest-cov <http://pypi.python.org/pypi/pytest-cov>`_,
  `coverage <http://pypi.python.org/pypi/coverage>`_, and
  `tox <http://pypi.python.org/pypi/tox>`_.
  Packaging linting with `pyroma <https://pypi.python.org/pypi/pyroma>`_.

* Thanks to Travis CI, successfully packaged for, and tested against, all
  reasonably late-model versions of Python: 2.6, 2.7, 3.2, 3.3, 3.4, 3.5, 3.6,
  and 3.7, as well as PyPy 5.8.0 (essentially Python 2.7.13) and PyPy3 5.10.1
  (corresponding to Python 3.5.3).

* The author, `Jonathan Eunice <mailto:jonathan.eunice@gmail.com>`_ or
  `@jeunice on Twitter <http://twitter.com/jeunice>`_
  welcomes your comments and suggestions.

Installation
============

To install or upgrade to the latest version::

    pip install -U chainmap

To ``easy_install`` under a specific Python version (3.3 in this example)::

    python3.3 -m easy_install --upgrade chainmap

(You may need to prefix these with ``sudo`` to authorize
installation. In environments without super-user privileges, you may want to
use ``pip``'s ``--user`` option, to install only for a single user, rather
than system-wide.)
