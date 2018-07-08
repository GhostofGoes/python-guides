.. header::

   Various useful snippets of Python code.



Time asyncio functions
======================

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



