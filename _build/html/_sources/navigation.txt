Navigation
===============

Change Directories with CD
-----------------------------
Glue includes its own version of the ``cd`` command.  Use the following syntax:

.. code::

	$ cd <directory-path>

To navigate to a parent directory, use the following idiom:

.. code::

 	$ cd ..

And to navigate to your user home directory (platform dependent), use this idiom:

.. code::

 	$ cd ~

Glue maintains the state of your working directory between command runs *while you keep the Glue view open*.  When you close the Glue view or use the ``exit`` command, this information is discarded and you start fresh the next time that you open Glue.

The Working Directory
------------------------
Your initial working directory differs based upon how you launch Glue.

Sidebar Right Click Menu Working Directory
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When you launch Glue with the right click menu over any of your project files or the root project directory, the root project directory is used as the working directory.

If you launch Glue in this fashion over a subdirectory, then the subdirectory is used as the initial working directory.

Command Palette Working Directory
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When you launch Glue with the Command Palette with a project file open in the editor, the root project directory is defined as the working directory.

Note that if you do not have a project file open in the editor, even if a project is open and in view on the sidebar, your initial working directory is set to your User directory as defined by the `Python os module expanduser method <http://docs.python.org/2/library/os.path.html?highlight=os.path#os.path.expanduser>`_:

.. code:: python

	os.path.expanduser("~")

This is the result of how Sublime Text handles file paths for new buffers that are opened in the editor.  Glue doesn't have access to the project directory path from the Command Palette unless a project file view is open in the editor.
