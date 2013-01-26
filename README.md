# Automatic Git Version in CMake and CPack

This is an example of automatically generating the version number for a
CMake[1] based project from the value returned by `git describe`.  This
version number is used for the version returned by a c program and
the version used by CPack when packaging the source and binary
distributions.

The version generation should work for in-source and out-of-source builds
from the git repository and from source packaged by CPack.

To support builds from source packages a `VERSION` file is included when
source distributions are generated by CPack.

*Note* this requires that `git describe` can describe something.  Thus,
there must be at least one annotated tag in the git repository (see the
`-a` and `-s` options to `git tag`).

## Example usage

In-source build from the git repository:

    git clone https://github.com/lcw/cmake_git_version.git
    cd cmake_git_version
    cmake .
    make

Out-of-source build from the git repository:

    git clone https://github.com/lcw/cmake_git_version.git
    mkdir build
    cd build
    cmake ../cmake_git_version
    make

Generate a source package from an out-of-source build run:

    make dist

Generate a binary package:

    make package

Build from the source package:

    tar xzvf VERSIONHEADER-0.1.0-2-gaae0565-Source.tar.gz
    cd VERSIONHEADER-0.1.0-2-gaae0565-Source
    cmake .
    make

## Acknowledgements

This is an example I have cobbled together from various code snippets in
emails to the CMake mailing list including [2] and [3] among others.

[1]: http://www.cmake.org/
[2]: http://www.cmake.org/pipermail/cmake/2010-July/038015.html
[3]: http://www.cmake.org/pipermail/cmake/2011-January/041870.html
