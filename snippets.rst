.. header::

   Various useful snippets of Python code.



Time execution of asyncio functions
===================================

.. code-block:: python

   >>> import time
   >>>
   >>> def timeit(coro):
   ...     async def timer(*args, **kwargs):
   ...         start = time.time()
   ...         result = await coro(*args, **kwargs)
   ...         print(f'Timed {coro.__name__}: {time.time() - start}')
   ...         return result
   ...     return timer
   ...
   >>> @timeit
   ... async def sleep_for(n):
   ...     await asyncio.sleep(n)
   ...
   >>> import asyncio
   >>> asyncio.get_event_loop().run_until_complete(sleep_for(5))
   Timed sleep_for: 5.000919342041016

Credit to: ``ava#4982``

Time execution of a standard function
=====================================

.. code-block:: python

   def time_execution(func):
      """Function decorator to time the execution of a function and log to debug.
      :param func: The function to time execution of
      :return: The decorated function"""
      from timeit import default_timer
      def wrapper(*args, **kwargs):
         start_time = default_timer()
         ret = func(*args, **kwargs)
         end_time = default_timer()
         logging.debug("Elapsed time for %s: %f seconds", func.__name__,
                        float(end_time - start_time))
         return ret
      return wrapper

Credit to: http://stackoverflow.com/a/15707426/2214380



Parsing YAML files with PyYAML
==============================
`PyYAML Reference <http://pyyaml.org/wiki/PyYAMLDocumentation>`_

.. code-block:: python

   from yaml import load, YAMLError
   try:  # Attempt to use C-based YAML parser if it's available
      from yaml import CLoader as Loader
   except ImportError:  # Fallback to using pure Python YAML parser
      from yaml import Loader

   def parse_yaml(filename):
      """Parses a YAML file and returns a nested dictionary containing its contents.
      :param str filename: Name of YAML file to parse
      :return: Parsed file contents"""
      try:
         # Enables use of stdin if '-' is specified
         with sys.stdin if filename == '-' else open(filename) as f:
               try:
                  # Parses the YAML file into a dict
                  return load(f, Loader=Loader)
               except YAMLError as exc:
                  logging.critical("Could not parse YAML file %s", filename)
                  if hasattr(exc, 'problem_mark'):
                     # Tell user exactly where the syntax error is
                     mark = exc.problem_mark
                     logging.error("Error position: (%s:%s)",
                                    mark.line + 1, mark.column + 1)
                  else:
                     logging.error("Error: %s", exc)
                     return None
      except FileNotFoundError:
         logging.critical("Could not find YAML file for parsing: %s", filename)
         return None


Links & Resources
=================
`KnownError's Python snippets <https://gist.github.com/GhostofGoes/e049e1cad17428194a3d8adaaaa7b392>`_ 

