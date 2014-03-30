File Management
==================

Glue includes commands that allow you to open files in the Sublime Text editor by path or wildcard.

Open Files by Path
--------------------

To open files by filepath, use the ``glue open`` sub-command with one or more filepath arguments:

.. code:: bash

	█ glue open <file> [file]

For example, to open the files ``test.txt`` and ``test2.txt`` from the current working directory in the editor, use the following command:

.. code:: bash

	█ glue open test.txt test2.txt


Open Files by Wildcard
------------------------

To open files by wildcard value, use the ``glue wco`` sub-command with a wildcard argument:

.. code:: bash

	█ glue wco <wildcard>

The following example will open all Python ``.py`` files in the sub-directory ``src`` on Unix/Linux systems:

.. code:: bash

	█ glue wco '/src/*.py'


Create a New File
--------------------

Create a new file from the command line with:

.. code:: bash

	█ glue new


File Management with System Utilities
------------------------------------------

You can use system utilities to manage your project files with Glue just as you would from a separate terminal.

For example, on Linux/Unix systems ``rm <filepath>`` will delete a file and ``rm -rf <dirpath>`` will remove the directory on ``dirpath`` and all of its contents. ``touch <filepath>`` will create a new file.
