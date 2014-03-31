Glue
======

Join Your Shell & Sublime Text in Quasi-Perfect* Harmony
-------------------------------------------------------------
`Glue <https://github.com/chrissimpkins/glue>`_ is a cross-platform, `extensible`_ plug-in for `Sublime Text 2 and 3 <http://www.sublimetext.com/>`_ that connects your favorite editor to your shell.

Launch
--------

**Use the right click menu in your project sidebar:**

.. image:: _static/images/popup-open-glue.png

**the Command Palette:**

.. image:: _static/images/command-palette-open.png

**or a keybinding:**

.. code:: bash

   Ctrl - Alt - G


Enter Commands
-----------------
Use the command input box at the bottom of the screen to enter system commands just like you would in your terminal:

.. image:: _static/images/command-entry-example.png

and the standard output is displayed in an editor view.

System Utilities
---------------------
It works with system utilities:

**grep**

.. image:: _static/images/grep-example.png

**curl**

.. image:: _static/images/curl-example.png


Scripting Languages
----------------------
It works with scripting languages:

.. image:: _static/images/scripting-language-example.png


Inter-Process Communication
---------------------------------------
Pipelining data between processes works.  You get the standard output from the final executable in the sequence:

.. image:: _static/images/pipelining-examples.png


Version Control
-------------------
Version control tasks are accessible inside the editor:

.. image:: _static/images/git-example.png


Compile, Unit Test, Profile, Minify, Compress...
--------------------------------------------------------------------
You get the picture.


Navigation & Working Directory State
---------------------------------------------------------
Glue includes its own version of the ``cd`` command that allows you to navigate around your directory structure while maintaining your current working directory state between calls to the shell.  See the `Navigation documentation`_ for details.

File Management
------------------
Open files in the Sublime Text editor by file path:

.. code::

	█ glue open <filepath> [filepath2] [...]

or by wildcard pattern:

.. code::

	█ glue wco <wildcard>

And create new files with:

.. code::

   █ glue new


Extend Sublime Text With Glue Extensions
-------------------------------------------
You can build Sublime Text extensions **with your favorite language** or extend Sublime Text **with any system utility** using Glue command extensions.  These are aliases for system commands that can be called from the Glue command line using the syntax:

.. code::

	█ glue <your-command> [optional arguments]

You have the option to pass additional command line arguments, clipboard data, or the current working directory path to the mapped system command with `template tags`_.

The Glue-Commands Directory
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create a directory in your Sublime Text ``Packages`` directory (``Preferences > Browse Packages``) that is named ``Glue-Commands``.

The glue.json File
^^^^^^^^^^^^^^^^^^^^^

Create a new file in this directory with the following path ``Glue-Commands/glue.json``.

Use the ``glue.json`` file to create Glue extensions with ``key = command name`` to ``value = command string`` mapping.

Example
^^^^^^^^^^

You could make a command that executes a local image compression shell script on the path ``/Users/me/scripts/cruncher.sh`` with the following syntax:

.. code:: json

   {
      "crunch": "/Users/me/scripts/cruncher.sh {{args}}"
   }

Then use it in Glue like this:

.. code::

	█ glue crunch image.png

The mapped system command is executed as:

.. code::

   /Users/me/scripts/cruncher.sh image.png

in your current working directory and is accessible in any Sublime Text project.

Make as many as you'd like.  You can use the following command to reference an alphabetized list of your extensions:

.. code::

   █ glue user

More detailed extension documentation (including additional examples) is `available here`_.


Limitations
-------------

✱ Glue communicates with your existing shell and there is no persistence of the data stream after your command is executed.  See the `limitations`_ that result from this application structure.

Contents
----------

.. toctree::
   :maxdepth: 2

   install
   navigation
   file-management
   extend-glue
   limitations
   issues
   contribute
   license

.. _limitations: limitations.html
.. _available here: extend-glue.html
.. _Navigation documentation: navigation.html
.. _extensible: extend-glue.html
.. _template tags: extend-glue.html#define-your-command-extensions

