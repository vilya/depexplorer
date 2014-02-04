depexplorer
===========

This is a simple tool which gives you an interactive command line for
exploring the dependencies between modules in your c and c++ source code.

You give it a list of modules and their roots and it will scan those
directories to find all the source and header files they contain, then parse
each of them for #include statements. If the #include resolves to a file from
another module, that's treated as a dependency.


Running
-------

If the script is in your path & has execute permission:

    depexplorer [ <file-or-dir> ]

The _file-or-dir_ argument is optional. It can be either the path to a module
list file (see below) or to a directory. If it's a directory, then we will
check for the module list file inside that directory; if it doesn't exist
there, we'll look in the parent directory; and so on, until we reach the root
of the filesystem.

If you don't provide the _file-or-dir_ argument, we search upwards from the
current working directory.

Note that unless you specify a filename explcitly on the command line, we
assume that the module list file is named "modules.txt".


The module list file
--------------------

This is a simple text file which tells depexplorer both where to find your
source code and how it's divided up into modules.

Each line of the file has the form

    <module-name> <module-root>

Where _module-name_ is a short displayable name for the module, which you can
use as input to the various commands which take modules as arguments; and
_module-root_ is the path to the root directory containing the module's source
code. If the module root is a relative path, it's treated as relative to the
directory containing the module list file.

We assume that module roots don't overlap at all. That is, you can't
have a module inside another module, or two modules with the same root.

At the moment a module can only have one root directory. Adding support for
multiple roots per module is on the todo list.


Using
-----

When you run depexplorer, you'll see a prompt. There's an interactive help
system which can provide information on the available commands and list all of
the known modules:

    depexplorer> help
    Enter 'help commands' to get a list of the available commands.
    Enter 'help modules' to get a list of the available modules.
    Enter 'help <command name>' to get info about a specific command.
  

Bugs, feedback and contributions
--------------------------------

The project page for this script is:

    https://github.com/vilya/depexplorer

If you have any bug reports or suggestions, please use the issue reporting
system there.

Feel free to fork this code and do what you like with it. Any pull requests will
be gratefully received!

