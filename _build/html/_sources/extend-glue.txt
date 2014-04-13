Extend Glue
=============

Glue allows you to extend the Sublime Text editor with system utilities, your own compiled executables, shell scripts, and source from any scripting language that is supported on your machine.

This is performed with Glue extensions that function as system command aliases and can be called from the command line with the syntax:

.. code:: bash

	█ glue <your-command> [args]

They are incredibly simple to develop and require absolutely no programming knowledge (but can be hooked into anything that you develop with the capability to process data from the standard input stream):

Create the Glue-Commands Directory
-------------------------------------
Create a ``Glue-Commands`` directory inside your Sublime Text ``Packages`` directory.   You can open your Sublime Text ``Packages`` directory with the menu item ``Preferences > Browse Packages``.

Create a glue.json File
-------------------------

Create a ``glue.json`` file inside the ``Glue-Commands`` directory.

Define Your Command Extensions
----------------------------------

Commands are defined in the ``glue.json`` file with a simple mapping of JSON key:value pairs using the following syntax

.. code:: json

	{
	 	"<command-name-1>": "<system command string 1>",
	 	"<command-name-2>": "<system command string 2>",
	 	[...]
	}

You have the option to include these replacement tags in your system command string:

==================   =============================================================
Template Tag          Definition
==================   =============================================================
``{{args}}``       	 additional arguments that you include on the command line
``{{clipboard}}``    the contents of the clipboard
``{{pwd}}``          the current working directory path
==================   =============================================================

These extensions are immediately available when you save the ``glue.json`` file.

.. note::

	Windows users should include single quotes around the ``{{pwd}}`` tag in the ``glue.json`` file.  Failure to do so will result in missing directory path separators in the path string that is replaced at the site of your template tag.  See `this issue report in the GitHub repository <https://github.com/chrissimpkins/glue/issues/1>`_ for more details.

Use Your Extensions
---------------------

Launch Glue and run your command extension(s) with the following syntax:

.. code:: bash

	█ glue <command-name> [args]

Your command is executed from your current working directory and data from the standard output stream (and standard error stream for any non-zero exit status codes) are displayed in the Glue view.


System Utility Example
------------------------
Let's make a command that allows us to view HTTP GET response headers for a web application that we are developing and call it ``head``.  We'll use cURL for this task.

Add the following to your ``glue.json`` file:

.. code:: json

	{
		"head" : "curl -I -s -L {{args}}"
	}

Save the file and the command is immediately available for use.  Launch Glue and enter any URL as an argument to your command in order to see the GET response headers for the site in the Glue view:

.. code:: bash

	█ glue head www.supafresh.com


Launch URL in Default Browser Example
----------------------------------------
The ``glue browse`` command opens a URL in your default browser.  Let's make an extension that performs a Google search for a query that we enter on the command line:

Add the following to your ``glue.json`` file:

.. code:: json

	{
		"google" : "glue browse https://www.google.com/#q={{args}}"
	}

Save the file and then use the command with a URL encoded query like this:

.. code:: bash

	█ glue google sublime+package+control


Multiple Application Version Example
----------------------------------------
You can alias multiple versions of an application so that you can easily access them for testing purposes.  Let's create extensions for recent versions of Python 2 & 3:

For Windows users, you can add the following to your ``glue.json`` file (assuming these are the appropriate versions and install paths):

.. code:: json

	{
		"py27" : "C:\\Python27\\python.exe {{args}}",
		"py33" : "C:\\Python33\\python.exe {{args}}",
		"py34" : "C:\\Python34\\python.exe {{args}}"
	}

Note the escaped backward slashes in the path string.

And Mac OSX users who install Python with Homebrew can create their extensions like this:

.. code:: json

	{
		"py27" : "/usr/local/Cellar/python/2.7.6/bin/python {{args}}",
		"py33" : "/usr/local/Cellar/python3/3.3.5/bin/python3.3 {{args}}",
		"py34" : "/usr/local/Cellar/python3/3.4.0/bin/python3.4 {{args}}"
	}

Confirm the above filepath settings on your own machine.

Then use the separate versions of Python with the following commands:

.. code:: bash

	█ glue py27 --version
	Python 2.7.6

	█ glue py33 --version
	Python 3.3.5

	█ glue py34 --version
	Python 3.4.0


Shell Script Example
---------------------

For the shell script example, we will make a JavaScript minifier and obfuscator command that is hooked into the YUICompressor.  If you are following along, you can download YUICompressor from `the GitHub repository`_.  You will need to have Java version 1.4+ installed to use it.  Unpack the repository and move the ``yuicompressor-2.4.8.jar`` file to a directory for safe keeping (you will run it from this directory).

Next, create a shell script named ``minijs.sh``.  Include the following script and modify the YUI_PATH variable with the actual path to your YUICompressor jar file:

.. code:: sh

		#!/bin/sh

		# Modify YUI_PATH with the path to the yuicompressor jar file
		YUI_PATH="path/to/yuicompressor-2.4.8.jar"

		if [ $# -eq 0 ]; then
		  echo "Please include the file path(s) for the file(s) that you would like to compress." 1>&2
		  exit 1
		fi

		for file in "$@";
		do
		if [ -f "$file" ]; then
		      java -jar "$YUI_PATH" -o "${file%%.*}-min.js" "$file"
		      if (( $? )); then
		          echo "$file was not able to be minified"
		          exit 1
		      else
		          echo "$file was minified to ${file%%.*}-min.js"
		      fi
		  else
		      echo "Unable to find the javascript file '$file'."
		fi
		done;
		exit 0

The script confirms that the filepath argument is a file, then minifies and obfuscates the JavaScript in the file.  It will work with more than one file if you pass multiple files to it in your command.  The minified version is renamed to ``<originalname>-min.js`` and saved to the same directory as the original JavaScript file.

Next, create a Glue extension that will serve as an alias for the call to this shell script when you use the ``glue minijs`` command.  We'll include the ``{{args}}`` template tag so that we can pass filepath arguments to our script:

.. code:: json

	{
		"minijs" : "/path/to/minijs.sh {{args}}"
	}

Launch Glue in your editor and minify JS files in the working directory with a command like this:

.. code:: bash

	█ glue minijs awesome.js

The minified file is saved as ``awesome-min.js`` in the same directory.


.. _the GitHub repository: https://github.com/yui/yuicompressor


