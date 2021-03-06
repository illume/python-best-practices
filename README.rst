Some guide lines for python best practices.


Testing
=======

Use pytest because

- No boilerplate
- Failure reports
- Scalability
- Fixtures
- Mocking/Monkeypatching
- Mature with great plugins


Integration tests
-----------------

Separate integration (functional) tests from unit tests.

Unit tests should be quick to run, and integration tests should
test the integration with external APIs or systems.


Code coverage
-------------

Use code coverage reporting to make sure code is at least tested.
Track and enforce a minimum standard in CI.


Documentation
=============

Write documentation with
`Sphinx
<http://www.sphinx-doc.org/en/stable/index.html>`_ and RestructuredText.

You can write narative style documentation, and also generate API documentation.


Type documentation
------------------

Document types with the typing module, rather than specify them in docstrings.
Because then the types can be checked with a tool called mypy in CI and in some code editors.

From sphinx-autodoc-typehints `sphinx-autodoc-typehints
<https://github.com/agronholm/sphinx-autodoc-typehints>`_ ...

.. code-block:: python

	from typing import Union

	def format_unit(value: Union[float, int], unit: str) -> str:
	    """ Formats the given value as a human readable string
	        using the given units.

	    :param value: a numeric value
	    :param unit: the unit for the value (kg, m, etc.)
	    """
	    return '{} {}'.format(value, unit)


There is an `example of how to document your python functions
<https://thomas-cokelaer.info/tutorials/sphinx/docstring_python.html>`_


Literate programming
====================

Experiments and live documentation can be done with
`jupyter notebooks
<http://jupyter.org/>`_

This is a great tool for experiments, notebooks, and live documentation, and visualizations.


Code quality and formatting
===========================

Use `pylint
<https://www.pylint.org/>`_
for linting, and `black
<https://github.com/ambv/black>`_
for code formatting.

Especially for developers new to python, pylint gives a lot of
good advice on how to improve your code.

It can catch many simple errors before they get checked into
source control or go into production.

A code formatter like `black
<https://github.com/ambv/black>`_
is useful in large teams so as to avoid having to talk about code formatting.


Package your code
=================

The `python packaging guide
<https://packaging.python.org/>`_
explains how to package python code.

- share your code with others
- a file structure all tools expect


A private python index
======================

Private Python packages can be stored in a private python index.
`devpi
<https://devpi.net/docs/devpi/devpi/stable/%2Bd/index.html>`_

Devipi is also useful because it can act as a local mirror and cache.
This can make deploys quicker and more reliable.


Manage dependencies
===================

With `pip
<https://pip.pypa.io/en/stable/>`_.

Working inside a virtual environment to keep projects separated.
Because each project may require different dependencies
installing them system wide will not work.

