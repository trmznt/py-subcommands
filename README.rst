py-subcommands
==============

This is a python modules for sub-commands CLI with bash autocomplete.

Sub-commands are useful for minimizing name collisions between executables.
For example, instead of having several executables in path such as ``my-app-init``,
``my-app-run``, ``my-app-list``, etc, we can have a single executable ``my-app`` with
``init``, ``run`` and ``list`` as its subcommands, eg: ``my-app init``.

With this library, each sub-command would be coded as individual script under a module path.
The library only consists of a single Python module file, and this module file can be dropped
to any of python library path to be used directly.
