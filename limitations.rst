Limitations
================

Glue and Your Shell
-----------------------

Glue is a non-interactive interface to your system shell.  This means that Glue communicates with your shell and the data stream is disconnected when the standard output or standard error data are returned to Glue.

This application structure leads to some limitations that differ from your traditional terminal emulator.  In the following cases, you will need to return to your system terminal:

1. Use commands that require you to submit a superuser password
2. Respond to standard input prompts from command line applications


