py-subcommands
==============


Introduction
------------

This is a python modules for sub-commands CLI with bash autocomplete.

Sub-commands are useful for minimizing name collisions between executables.
For example, instead of having several executables in path such as ``my-app-init``,
``my-app-run``, ``my-app-list``, etc, we can have a single executable ``my-app`` with
``init``, ``run`` and ``list`` as its subcommands, eg: ``my-app init``.

With this library, each sub-command would be coded as individual script under a module path.
The library only consists of a single Python module file, and this module file can be dropped
to any of python library path to be used directly.


Quick Start
-----------

To use the library, create a python main script (that are accessible from PATH), such as
the following ``my-app.py`` script:

.. code-block:: python

	#!/usr/bin/env python3
	# PYTHON_ARGCOMPLETE_OK

	from subcommands import SubCommands

	if __name__ == '__main__':

		SubCommands(
			modules=['my_app.cmds'],
		).main()

	# EOF

Run the ``argcomplete`` command to register ``my-app.py`` script for tab-completion::

	eval "$(register-python-argcomplete ngs-pl)"

Alternatively, active the global completion by running the following command::

	activate-global-python-argcomplete

In ``my_app/cmds`` directory, create the sub-command script, such as the following
``init_data.py`` script:

.. code-block:: python

	# this script implement init-data command

	import argparse

	def init_argparser():

		p = argparse.ArgumentParser()
		p.add_argument('infile')
		return p

	def init_data(args):
		print('Initializing data...')

	def main(args):
		init_data(args)

	# EOF

The ``init-data`` sub-command can now be executed as following::

	my-app.py init-data

