This repository combines all the various tools and libraries needed for building super_prove.

# Binaries

Recent builds should be available at our [downloads](http://downloads.bvsrc.org/super_prove/) page.

# How to build this tool #

## Requirements

* CMake 3.3 or above
* Ninja build tool
* g++ 4.8 or above (or clang with similar levels of C++11 support)
* Python 2.7 with development headers and libraries
* Python setuptools
* Mercurial

For example, in Ubuntu 16.04, run the following command to satisfy all the requirements:

    sudo apt-get install cmake ninja-build g++ python-dev python-setuptools mercurial

Note that the version of CMake included in previous Ubuntu releases is too old. This requires CMake 3.3 or later to be manually installed.

## Checking out the code ##

This repository uses Mercurial subrepositories to collect a few repositories with the code required to build this tool

    hg clone https://bitbucket.org/sterin/super_prove_build

This will checkout all the relevant subrepositories

## Building the tool ##

Create a build directory:

    mkdir build

Change into the new directory:

    cd build

Configure:

    cmake -DCMAKE_BUILD_TYPE=Release -G Ninja ..

(replace .. with the top-level featrues_build directory)

Build:

    ninja

Create a package:

    ninja package

This will create a super_prove_<version>-<OS>-Release.tar.gz in the build directory.

# How to run this tool #

Extract the .tar.gz file and runRun the `run.sh` script in the `bin` subdirectory

    super_prove/bin/super_prove.sh [-n] <some_aig_file.aig>

Try the `--help` flag to see the available options.
