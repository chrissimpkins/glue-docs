Commands
============

Table of Commands
-------------------

====================   ================================================================
 Command                Description
====================   ================================================================
``cd``					change working directory
``exit``       	 		exit Glue
``glue browse``    		open URL or local project file in default browser
``glue clear``          clear the text in the Glue view
``glue finder``         reveal current directory (default) or optional path in finder
``glue help``			open the Glue help in the Glue view
``glue localhost``      open webbrowser to local server (default port 8000)
``glue new``			open a new Sublime Text buffer
``glue open``			open one or more project files by filepath
``glue path``			display the system PATH setting that is used by Glue
``glue user``			display an alphabetized list of Glue user extensions
``glue wco``			open one or more project files by wildcard pattern
====================   ================================================================

Command Usage
----------------

⊙ ``cd``
---------
Change the working directory.  Directory state is maintained between calls to the shell until you submit the command ``exit``.  This works on Unix, Linux, and Windows platforms.

**Usage**

Navigate to user assigned directory:

.. code::

	cd <directory path>

Idiom for navigation to parent directory:

.. code::

	cd ..


⊙ ``exit``
------------
The ``exit`` command performs cleanup tasks and exits the Glue terminal.  The view is not automatically closed.

**Usage**

.. code::

	exit


⊙ ``glue browse``
-------------------
Open a URL ``<url>`` or a local project filepath ``<path>`` in the default web browser.

**Usage**

.. code::

	glue browse <url, path>


⊙ ``glue clear``
-------------------
Clear the text in the Glue view.

**Usage**

.. code::

	glue clear


⊙ ``glue finder``
------------------------
Reveal the current working directory or optional directory path in the finder

**Usage**

Reveal current working directory in finder:

.. code::

	glue finder

Reveal ``subdirectory`` path in finder:

.. code::

	glue finder [subdirectory]


⊙ ``glue help``
------------------
Open the Glue help in the Glue view.

**Usage**

.. code::

	glue help


⊙ ``glue localhost``
-----------------------
Open the default web browser to the local server at the URL http://localhost:8000 by default.  You have the option to assign the port in your command.

**Usage**

.. code::

	glue localhost [port]


⊙ ``glue new``
-----------------
Open a new Sublime Text buffer in the editor.

**Usage**

.. code::

	glue new


⊙ ``glue open``
------------------
Open one or more files in the Sublime Text editor by filepath.

**Usage**

.. code::

	glue open <filepath> [, filepath]


⊙ ``glue path``
------------------
Display the system PATH that is used by Glue

**Usage**

.. code::

	glue path


⊙ ``glue user``
----------------
Display an alphabetized list of your Glue user extensions

**Usage**

.. code::

	glue user


⊙ ``glue wco``
-----------------
Open one or more files in the Sublime Text editor by wildcard pattern

**Usage**

.. code::

	glue wco <pattern>


