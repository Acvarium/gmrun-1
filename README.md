GMRUN
-----
A run utiliy featuring a slim design and bash style auto-completion. 

Features
---------

    * Tilda completion (~/ <==> $HOME/)

    * Completion works for separate words (e.g. you can type em<TAB> which
      turns to emacs, type a SPACE, and write the file you want to open using
      completion).

    * Configuration file: ~/.gmrunrc or /etc/gmrunrc.
      Check one of them, configuration is very simple. From that file you
      can change window position and width, history size, terminal, URL
      handlers, etc.

    * CTRL-Enter runs the command in a terminal.
    * CTRL-Enter without any command starts a new terminal.

    * History is maintained in the file "~/.gmrun_history".

    * CTRL-R to search backwards through history.
    * CTRL-S to search forward through history.
    * "!" enters a special search mode, matching only the start of strings.
    -- Esc to cancel search (only once).

    * URL handlers allowing you to enter lines like "http://www.google.com"
      to start your favorite browser on www.google.com.
      The URL-s are configurable from the configuration file.

    * Extension handlers.  Basically you can run, for instance,
      a ".txt" file, assuming that you have configured a handler for it
      in the configuration file.


Requirements
-------------

    * GTK 2/3


Compilation, installation
--------------------------

    Use the configure script (run ./autogen.sh if ./configure is missing):

        ./configure --prefix=/usr --sysconfdir=/etc
        make
        make install

    Pass --enable-gtk3 to ./configure to build the gtk3 ui

    Optionally you can configure your window manager to call gmrun
    with WinKey + R or something.


Tips and tricks
---------------

1. Everything that doesn't start with "/" or "~" gets completed from $PATH
   environment var.  More exactly, all files from $PATH directories are
   subjects to completion (even if they are NOT executables; this is a
   bug, but I'm afraid I'm not willing to fix it).

   Pressing TAB once when no text is entered opens the completion window,
   which will contain ALL files under $PATH.

2. For instance you use TAB to complete from "nets" to "netscape-navigator".
   A small window appears, allowing you to select from:

       - netscape
       - netscape-navigator
       - netstat

   That is because all these executables have the same prefix, "nets".  You
   type TAB twice to get to the third element ("netscape-navigator").  Now,
   if you want to add a parameter, press SPACE (the list disappears,
   and a SPACE is inserted after the netscape-navigator).

   You can use UP / DOWN arrows to select the right completion.

3. - ESC closes the completion window, leaving the selected text in the entry.
   - HOME / END - the same, but clears the selection.
   - SPACE - the same, but clears the selection and appends one space.
   - Pressing ENTER (anytime) runs the command that is written in the entry.
   - Pressing CTRL+Enter (anytime) runs the command in a terminal (check your
     configuration file).  But if the entry is empty (no text is present, or
     only whitespaces) then a fresh terminal will be started.
