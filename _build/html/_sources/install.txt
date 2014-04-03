Install Glue
==============

Install with Sublime Package Control
--------------------------------------

If you use `the Sublime Package Control system <https://sublime.wbond.net/>`_, you can install Glue with the Sublime Text Command Palette. Open it with:

**Mac OSX**

.. code::

	Cmd - Shift - P

**Linux/Windows**

.. code::

	Ctrl - Shift - P


Type 'install', select the menu item, ``Package Control: Install Package``, then type 'glue'.  The selection for the Glue plugin will appear. Select it and the install is performed automatically.


Install with Git
-----------------

Open your ``Packages`` directory with the Sublime Text menu items ``Preferences -> Browse Packages``.  Then git clone the Glue repository as a new directory named 'Glue' in your Packages directory with the following command:

.. code::

	█ git clone https://github.com/chrissimpkins/glue.git "Glue"


Manual Install
----------------
If you like to do things the good ole' fashion way, download the source repository from GitHub (`tar.gz <https://github.com/chrissimpkins/glue/tarball/master>`_ | `zip <https://github.com/chrissimpkins/glue/archive/master.zip>`_).

Decompress the source repository and rename it "Glue".

Open your Sublime Text Packages directory using the ``Preferences -> Browse Packages`` menu items.

Move the entire Glue directory into your Sublime Text Packages directory.


Confirm Your PATH
------------------

Glue assigns a default user PATH from your environment PATH variable.  Frequently, it nails it, but on some installs it may require a bit of help (generally the case for Mac OSX users because of an issue with the assignment that takes place in this version of Sublime Text).  Never fear.  It is incredibly simple to correct this issue.

Confirm that the correct string is being used by launching Glue (use one of the approaches below) and entering the command:

.. code:: bash

	glue path

in the text input box at the bottom of your editor.  This displays the default PATH that Glue uses to identify your executable files.  If the PATH is incorrect, or if you simply want to modify your PATH in Glue, follow the instructions below.

Change Your PATH Settings
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Open the Glue user settings file by using the Sublime Text menus to navigate to ``Preferences > Glue > Glue Settings - User``.  Include the following line in your JSON settings:

.. code:: json

	{
		"glue_userpath" : "<YOUR PATH>"
	}

Include your shell PATH settings as a colon (Unix/Linux) or semicolon (Windows) delimited string.  Linux/Unix (including Mac OSX) users can find this by entering ``echo $SHELL`` in the terminal.

Here is an example of an appropriate PATH setting for Unix/Linux users:

**Unix/Linux**

.. code:: json

	{
		"glue_userpath" : "/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
	}


Save the file and restart Sublime Text.

Windows users can enter the command ``ECHO %PATH%`` in cmd.exe to view their PATH string.  Enter this in the Glue settings file and escape the backward slash characters in the PATH string like this:

**Windows**

.. code:: json

	{
		"glue_userpath": "C:\\Windows\\system32;C:\\Windows;C:\\Windows\\System32\\Wbem;"
	}

Save the file and restart Sublime Text.

Glue respects your assignment of directory priority in the standard left to right sequence as it attempts to locate system executables for the commands that you submit.  If you find that a different version of an executable is being launched, or that installed applications are not being located, please confirm your PATH string in the Glue settings.

.. note::

	Use the ``Glue Settings - User`` settings file rather than the default file.  The default settings are overwritten on Glue updates!

Set Your Default Shell
-------------------------
You have the option to assign your default shell in the ``glue_shellpath`` setting.  Open the ``Glue Settings - User`` JSON file and add a new line to it that includes the setting key with the value set to the path to your desired shell.

Here's an example that demonstrates how to change the default shell to zsh on Unix/Linux boxes:

.. code:: json

	{
		"glue_shellpath": "/usr/local/bin/zsh"
	}

Save the file and restart Sublime Text. Note that the shell that is executed may differ from your environment ``$SHELL`` (Unix/Linux) or ``%SHELL%`` (Windows) setting.  The Glue settings change does not alter your system variable assignments, or your default system shell settings, in any way.  To confirm that it is working, type a command that will cause the shell to bark at you (e.g. an executable that doesn't exist):

.. code::

	█ boguscmd
	zsh:1: command not found: boguscmd

Set Your PS1
-------------
Give your prompt a little style.  Change the default by adding the ``glue_ps1`` setting to the ``Glue Settings - User`` file (see instructions above).  Here's an example that shows how to change it to a ✪

.. code:: json

	{
		"glue_ps1" : "✪"
	}

And here's what you get:

.. image:: _static/images/ps1-star-example.png


Get Started
-------------

You can open Glue with any of these approaches:

**Use the right click menu in your project sidebar**

.. image:: _static/images/popup-open-glue.png

**Use the Command Palette**

.. image:: _static/images/command-palette-open.png

**Keybinding**

.. code:: bash

	Ctrl - Alt - G

Then begin entering your commands in the command line at the bottom of the editor.

.. image:: _static/images/command-entry-example.png

Use the same syntax that you use on the command line in your terminal (with special character escapes or quotes!).



