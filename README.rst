Boost.Build files to build QuantLib without autotools
=====================================================

I tired of fighting autotools and libtool on MinGW so I decided to use
Boost.Build instead. Not that I liked it but it least it is more predictable.

I tested it on Windows and Linux.

Usage
-----

If you are on Windows, install `MinGW`_.

On all platforms, download and extract `boost`_ and `QuantLib`_.
Due to the specific version of GCC I needed, I used GCC-4.5.2 with boost-1.50
and QuantLib-1.2.1.

If you don't have Boost.Build (bjam) installed, run this in the Boost directory
ensuring *gcc* is in your PATH::

    cd tools\build\v2
    boostrap mingw
    .\b2 install --prefix=<your-preferred-dir-for-bjam>

The same will work on Linux if you replace backslashes in paths with forward ones.

Making sure *b2* is in PATH, adjust PATH to Boost in the ``use-project /boost`` line
of *jamroot.jam*.
The execute this in the QuantLib directory to build fully static library (*--hash*
is used to reduce command line length)::

    b2 -d+2 --hash

Also you might want to run the same in the *Examples* and *test-suite* directories.

Probably some time later I will add installation targets, for now the built library
can be used in place from *bin* subdirectories, see *test-suite/jamfile.jam* for how
you can refer QuantLib in your Boost.Build files.

.. _MinGW: http://mingw.org

.. _boost: http://boost.org

.. _QuantLib: http://quantlib.org
