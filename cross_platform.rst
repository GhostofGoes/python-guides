.. header::

   Cross-platform development tips and tricks.

General best practices
======================

Check your assumptions!
You can't assume anything about the shell (so a call to popen might not do what you expect). 
Don't rely on common commands, like ping, being available, or operating the same. For instance, `ping` on Windows 
will send 4 packets by default, while `ping` on Linux will continue forever, and the argument to configure how many 
are sent is different for each. Furthermore, on Windows IPv6 ping is `ping -6`, while on Linux it's `ping6`. 
And this is *just* ``ping``!

Unfortuantly, there isn't a silver bullet. When possible, use pure Python implementations of whatever 
it is you're trying to do, even if it means additional code or taking on an additional dependency. 
While it means some additional work up front, in the long run the benefits are worth it: your code is 
more portable, less brittle to changes or oddities in the platform or operating envrionment, and overall 
less of a hassle to maintain.

Going back to the ``ping`` example: examine why you're using ping. If you're just checking if the host is up, 
and don't need the other information `ping` provides (like latency), why not just use a TCP SYN check? It's 
faster, and much easier to implement.

 TODO: example code


Filesystems and paths
=====================
os.path vs pathlib.

how to use pathlib.
how to use os.path.
?? hackery with the internal ntpath/posixpath (example of why pathlib is nicer).


Dependencies
============
* Compiled portions of Dependencies
* Ensuring they support the platform




