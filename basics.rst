.. header::

* Collection of non-code stuff that's nice to know and is up to date, targeted to newbies. 
Want to try to ease over the often conflicting tribal knowledge found on SO/etc., 
and platform differences (e.g. use python -m pip install --user instead of pip install or sudo -H pip install)

Python Quickstart
=================

Install Python
++++++++++++++
Windows
OSX
Linux

Hello World!
++++++++++++


Basic concepts
==============


Lists
+++++

.. code-block:: python

   for item in list:
      print(item)


.. code-block:: python

   for index in range(len(list)):
      print(list[index])



Packages
========

What are packages?
++++++++++++++++++
What is a "package". 
Often referred to as "libraries" or "modules".
"modules" are not the same as "packages". 
What are the differences.


Installing Packages using ``pip``
+++++++++++++++++++++++++++++++++
What is pip?
What can you do with it?

`python -m pip install --user`
Doing the -m thingy gets you around annoying issues, and --user means you don't have to use sudo


Windows
Linux
OSX


ensurepip 
``python -m ensurepip`` (possibly as sudo)

apt/yum/dnf/zypper

The Ubuntu (and possibly Debian) special snowflake edge case.



