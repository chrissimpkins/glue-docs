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
``glue goto``           Sublime Text Goto Anything search
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
Change the working directory.  Directory state is maintained between calls to the shell until you submit the command ``exit``.  This command works on Unix, Linux, and Windows platforms.

**Usage**

**Navigate to user assigned directory**:

.. code:: shell-session

    █ cd <directory path>

**Idiom for navigation to parent directory**:

.. code:: shell-session

    █ cd ..

**Idiom for navigation to your platform-dependent user home directory**:

.. code:: shell-session

    █ cd ~


⊙ ``exit``
------------
The ``exit`` command performs cleanup tasks and exits the Glue terminal.  The view is not automatically closed.

**Usage**

.. code:: shell-session

    █ exit


⊙ ``glue browse``
-------------------
Open a URL ``<url>`` or a local project filepath ``<path>`` in the default web browser.

**Usage**

.. code:: shell-session

    █ glue browse <url, path>


⊙ ``glue clear``
-------------------
Clear the text in the Glue view.

**Usage**

.. code:: shell-session

    █ glue clear


⊙ ``glue finder``
------------------------
Reveal the current working directory or optional directory path in the finder

**Usage**

Reveal current working directory in finder:

.. code:: shell-session

    █ glue finder

Reveal ``subdirectory`` path in finder:

.. code:: shell-session

    █ glue finder [subdirectory]


⊙ ``glue goto``
-------------------
Launch the Sublime Text Goto Anything search feature with the query term, ``<file query>``

**Usage**

.. code:: shell-session

    █ glue goto <file query>

This works best if you use a part of a project filename or directory and submit the Glue command.  You will receive a list of matching files and can add additional symbols to jump to locations within the desired file.  Add the ``@`` character and additional text to your query to jump to symbols in the file.  Add the ``#`` character and additional text to the query to search within the file.  And add the ``:`` character followed by a numeral to jump to a line number in the file.

.. note::

    Sublime Text does not permit the searches within files using ``@``, ``#``, or ``:`` to be performed with this Glue command.  Add these search filters to your query once you identify the proper file in the list produced by the Goto Anything file match.


⊙ ``glue help``
------------------
Open the Glue help in the Glue view.

**Usage**

.. code:: shell-session

    █ glue help


⊙ ``glue localhost``
-----------------------
Open the default web browser to the local server at the URL http://localhost:8000 by default.  You have the option to assign the port in your command.

**Usage**

.. code:: shell-session

    █ glue localhost [port]


⊙ ``glue new``
-----------------
Open a new Sublime Text buffer in the editor.

**Usage**

.. code:: shell-session

    █ glue new


⊙ ``glue open``
------------------
Open one or more files in the Sublime Text editor by filepath.

**Usage**

.. code:: shell-session

    █ glue open <filepath> [, filepath]


⊙ ``glue path``
------------------
Display the system PATH that is used by Glue

**Usage**

.. code:: shell-session

     █ glue path


⊙ ``glue user``
----------------
Display an alphabetized list of your Glue user extensions

**Usage**

.. code:: shell-session

    █ glue user


⊙ ``glue wco``
-----------------
Open one or more files in the Sublime Text editor by wildcard pattern

**Usage**

.. code:: shell-session

    █ glue wco <pattern>


