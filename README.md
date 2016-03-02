Overview
--------

This is an example C++ project which uses the gflags library for the parsing of
the command-line flags. It demonstrates the use of either [Bazel](http://bazel.io/)
or [CMake](https://cmake.org/) for the build of the project where the source code
of the gflags library is optionally directly included in the example project's
source tree using the [Git submodule command](https://git-scm.com/docs/git-submodule).
When the submodule is not initialized, an external installation of the gflags
library is required instead.


Download
--------

Use the [git clone](https://git-scm.com/docs/git-clone) command to download this
gflags example project:

```
git clone --depth=1 https://github.com/gflags/example.git gflags-example
cd gflags-example
```

When gflags should be build as subproject of the example which does not
require an external installation of the gflags library, run the following
command in the top-level directory of the local Git repository after the
clone command. This is only recommended when CMake is used for the build
configuration and no separate gflags installation is available.

```
git submodule update --init
```


Build with CMake and GNU Make
-----------------------------

First, create a build directory inside the example project directory and
configure the build using [CMake](https://cmake.org) to generate the Makefiles
for [GNU Make](https://www.gnu.org/software/make/):
```
mkdir build && cd build
cmake ..
```

Then build the example executable named "foo" using GNU Make:
```
make foo
```

The resulting binary is ```bin/foo``` inside the build directory.


Build with Bazel
----------------

The [Bazel](http://bazel.io) build tool uses the information in the WORKSPACE file
to download and build the gflags library prior to the example binary. To build the
example executable target named "foo", run the following command in the top level
directory of the gflags example project which contains the WORKSPACE file.

```
bazel build \\example:foo
```

