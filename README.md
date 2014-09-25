Task Spooler
------------

This is a fork of [Task Spooler](http://vicerveza.homeunix.net/~viric/soft/ts/) by  **Lluís Batlle i Rossell** and yet only add a minimal **GNU/Autotools** support, and the helper/rules to build a **Debian** binary package, and a ruby Formula for (home)brew (Mac OS X).

"task spooler is a Unix batch system where the tasks spooled run one after the other. The amount of jobs to run at once can be set at any time. Each user in each system has his own job queue. The tasks are run in the correct context (that of enqueue) from any shell/process, and its output/results can be easily watched. It is very useful when you know that your commands depend on a lot of RAM, a lot of disk use, give a lot of output, or for whatever reason it's better not to run them all at the same time, while you want to keep your resources busy for maximum benfit. Its interface allows using it easily in scripts."

Notice: there's already an official Debian package named `task-spooler`, on installation the package generated by this fork will conflict.

For more information about what *Task Spooler* is or its usage please refer to the original website:

http://vicerveza.homeunix.net/~viric/soft/ts/

**Autotools**

To build and install, from the sources directory:

    mkdir build # the build directory is optional you may use ./configure
    cd build
    ../configure --prefix=/some/install/dir # default /usr
    make
    sudo make install

If there's any problem with distributed `configure` script or `Makefile.in` use the `autogen.sh` (autoreconf, autoconf, autoheader, aclocal, automake needs to be already installed)
     
     ../autogen.sh --prefix=/some/install/dir # autogen call configure once updated
     make
     sudo make install

**Debian**
To build the Debian binary package:
    
    fakeroot debian/rules binary
the package will be created in `../`, install it with:
     
     sudo dpkg -i ../ts_0.7.4-1_i386.deb # i386 is an example your arch may differ

**Brew** (Mac OS X)

    cp ts.rb /usr/local/Library/Formula/
    brew install ts

**Upstream**

*Task Spooler* may be still built using the original `Makefile`:

    make -f src/Makefile.noauto PREFIX=/some/install/dir
but in this case I would rather suggest to use the tarball distributed from the [upstream website](http://vicerveza.homeunix.net/~viric/soft/ts/).
