.. header::
   Guides on intermediate concepts and techniques, like 
   virtualenvs and altnerative intepreters. We recommend that 
   you a good grasp of the basics of Python and programming 
   before reading this.


Alternative Python Interpreters (PyPy, etc.)
=====================================
What are alternative interpreters?
What is CPython?

Why use an alternative interpreter?
+++++++++++++++++++++++++++++++++++


Examples of alternative Interpreters
++++++++++++++++++++++++++++++++++++
What are some examples?
   IronPython, Jython, PyPy


What's pypy, and when should you use it?
++++++++++++++++++++++++++++++++++++++++


Virtual Environments
====================
What are they useful for
* Isolating packages for a specific project from system packages (especially when it comes to versions!)
* Easily work with a specific version of Python
* Easier to work with other Python interpreters (like pypy)

Downsides
* Bit of work to setup and use (once you know the commands it's easy)
* Uses a bit of extra disk space

`Good overview of virtual environments <https://stackoverflow.com/a/41573588/2214380>`_

Make sure to add to `.gitignore` in a project. 
A good practice is to have a ``~/.virtualenvs`` or ``~/envs`` directory with all of your environments.

On Linux: ``source /path/to/environment/bin/activate``
On Windows: ``& \path\to\environment\Scripts\activate``

Create a Python 2 one: 
.. code-block: bash
   python -m pip install --user -U virtualenv
   python -m virtualenv ~/py2env
   source ~/py2env/bin/activate
Python 3:
..code-block: bash
   python3 -m pip install --user -U virtualenv
   python3 -m virtualenv --python=python3 ~/py3env
   source ~/py3env/bin/activate

virtualenvwrapper: Wrapper around virtualenv that provides some nice shortcuts and management capabilities 
(`link <http://virtualenvwrapper.readthedocs.io/en/latest/>`_)
Python 3's built-in ``venv`` (`link <https://docs.python.org/3/library/venv.html>`_)
pipenv (`link <http://docs.python-guide.org/en/latest/dev/virtualenvs/>`_)


Debugging
=========
* Debugging with `pdb`

Performance and optimization
============================
Considorations.
How to profile your program.


