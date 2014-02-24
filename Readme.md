Homerepo
--------

When working in an environment without admin permissions, it is sometimes
feasible to put software repositories in your *$HOME* folder and install them
locally. Homerepos job is to keep these up to date. It manages git, svn,
mercurial and cvs repositories by retrieving changes and (re-)building them to
update local installations.

Have fun and keep it local ;-).

Setup and Usage
---------------

Clone the repository and use it right away. For a more permament setup, drop
(or link) the homerepo script somewhere in *$PATH*.  At its first run, homerepo
creates '.config/homerepo/config' Please modify this short config file to
personal preferences.

Afterwards, 'homerepo upgrade' will upgrade all repositories either in the order
specified in *$_CONFDIR/order* or simply all existing directories found
in *$_SRCDIR*. To check the actually used order, see 'homerepo list'.

Local Software Install Help
---------------------------

Most software can be configured to install locally, e.g.:

    autotools: ./configure --prefix=$HOME/local
    cmake:     cmake -DCMAKE_INSTALL_PREFIX=$HOME/local

which requires some environment modifications for other programs and tools:

    export PATH="$PATH:$HOME/local/bin"
    export LIBRARY_PATH="$HOME/local/lib" # add e.g. lib32,lib64
    export LD_LIBRARY_PATH="$LIBRARY_PATH"
    export LD_RUN_PATH="$LIBRARY_PATH"
    export C_INCLUDE_PATH="$HOME/local/include"
    export CPLUS_INCLUDE_PATH="$C_INCLUDE_PATH"

