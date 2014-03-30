Limitations
================

Glue vs. Terminals/Shells
---------------------------

Glue communicates with your shell and the data stream is disconnected when the standard output or standard error data is returned to Glue.  It works well for one-off commands that do not require further input to complete the requested task.

This structure leads to a several limitations.  In the following cases, you will need to return to your terminal to perform the tasks:

1. Use commands that require you to submit a superuser password
2. Respond to standard input prompts from command line applications


