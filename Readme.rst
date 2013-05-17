Homerepo
=========

Homerepo manages git/svn/mercurial/cvs repositories. It pulls changes to the
repositories and, if necessary, builds them as well as updates their
installation.

Sometimes you work in an environment where you have no rights to install the
software you are used to work with or need to get your job done. So you start
to pull sources of different tools, configure them to install into your
*$HOME*, build and install them. How do you keep these up to date? Going
through all your installed software is way to tedious for more than just a
handful of tools.  But worry no more, this is exactly where homerepo comes in
handy.

Have fun and keep it local ;-).

------

Setup
======

Just clone the repository and use it right away (or get the homerepo script
here: https://raw.github.com/nilsonholger/homerepo/master/homerepo).  For a
more permament setup, just drop (or link) the homerepo script somewhere in your
*$PATH*.

At its first run, homerepo will create::

    .config/homerepo/config

Please modify the just created config file to your liking.

Most software can usually be configured to install locally::

    ./configure --prefix=$HOME/local
    cmake -DCMAKE_INSTALL_PREFIX=$HOME/local

which requiers to set some environment variables accordingly, so other programs
and tools will find these::

    export PATH="$PATH:$HOME/local/bin"
    export LIBRARY_PATH="$HOME/local/lib" # add e.g. lib32,lib64
    export LD_LIBRARY_PATH="$LIBRARY_PATH"
    export LD_RUN_PATH="$LIBRARY_PATH"
    export C_INCLUDE_PATH="$HOME/local/include"
    export CPLUS_INCLUDE_PATH="$C_INCLUDE_PATH"

------

Usage
======

**homerepo upgrade** will upgrade all repositories either in the specified
order from *$_CONFDIR/order* or simply all existing directories found in
*$_SRCDIR*. To check the currently used order, use **homerepo list**.
