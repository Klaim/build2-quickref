Quick Reference Of Build2 Commands
==================================

NOTE: Build2 version: v0.8.0

1 - Before using these commands
-------------------------------

1.0 - This reference document is designed to help non-power-users of build2 that need to use it irregularly or need to use it but don't need to do unusual commands.
It is not designed for experts.

1.1 - This reference document is **not a replacement** for the [build2 introduction](https://build2.org/build2-toolchain/doc/build2-toolchain-intro.xhtml) or for the [other documentation available on the website](https://build2.org/).
Please read at least the introduction first to understand the reasonning behind build2.

In particular, make sure you understand the differences between `b`, `bpkg`, `bdep` etc.

Don't hesitate to use help to get full manual of a command and see the other options:

    bdep help new  # for info about the `new` command of `bdep`

1.2 - This reference document is intended as a way to quickly remember how to do common
operations with build2. It could probably be made obsolete by ergonomy improvements
but build2's domain is so difficult to just solve that I believe it will take time to get there.

1.3 - These commands all assume that you are working **exclusively with `C++`**.
Somme commands options varies depending on the tools and languages you want to use with build2, which is language/tool agnostic by design, but still focuses first on the `C++`-specific problems.

1.4 - **On Windows, using Visual Studio compilers**: don't forget that `b` cannot yet automatically find the compiler version.
You need to launch all the commands from the Native Tools Command Prompot provided with your Visual Studio installs which provide one different for each compiler major version.
Personally I like to launch it and first call `powershell` to have some additional features.


2 - New Projects
----------------

2.1 - Create a new executable project with tests.

    bdep new myprojectname -t exe

2.2 - Create a new library project with tests.

    bdep new myprojectname -t lib

2.3 - Create a new project without creating libraries, executable or tests yet.

    bdep new myprojectname -t bare

2.4 - Create a multi-package repository.

2.4.1 - Create an empty repository ready to accept packages.

    bdep new myreponame -t empty

2.4.2 - Create a new packages inside the repository.

  Just add `--package` ot the `bdep new` commands done in the repository directory:

    cd myreponame
    bdep new myexepackage -t exe --package
    bdep new mylibrarypackage -t lib --package
    bdep new mynakedproject -t bare --package

3 - Setup Build Configurations
-----------------------------

NOTE: THIS PART IS NOT READY YET

As compiler name, version, compilation flags, linking flags etc varies depending on configurations, please refer to the documentation to get the one you want to use.

Here I will use `<my-options>` where there should be options like `config.cxx=cl` for example when using Visual Studio compiler. It is also ok to not specify options at first.


Also don't forget that these examples assume that we are manipulating `C` or `C++`projects, which is why the option `cc` is used here.

Please refer to the official documentation or commands manuals for additional details.

3.1. - Create a new build configuration for a project or repository.

  Note that the first configuration setup for a project will become it's default one.
  That do not provent a project to be setup to several different configurations.

3.1.1. With default config path directory that must not be in a project directory:

    cd myprojectrepo
    bdep init -C cc <my-options>


3.1.2. Specifying the config path directory that must not be in a project directory:

    cd myprojectrepo
    bdep init -C ../path-to-build-config-dir cc <my-options>

3.1. - Create a new build configuration for a project or repository.


