GCC6809 is distributed as a source patch against the mainline GCC sources.  It has not been integrated into the official releases, so you must first obtain the regular GCC sources, and then apply a patch which adds all of the 6809-related content.  Then you build and install the compiler itself.

## Patching the Sources ##

Because GCC6809 is just a patch file, you'll first
need to obtain an official release of GCC in source form, unpack it,
and apply the 6809 patch to produce the final source tree.
In order to build the cross-compiler, you'll need a working native compiler and some
other tools that are needed to build GCC, like _flex_ and _bison_.

You can obtain the regular GCC sources from
http://gcc.gnu.org/mirrors.html, which has links to many download
locations.  Look for a file named **gcc-_BASEVER_.tar.bz2** or similar.  Make sure that the source tarball and the patch have the same version number, aside from the patchlevel, which follows a dash.  Once you have the GCC source tarball and the GCC6809 patch, do the following:

  * First, extract the contents of the source tarball, using _gunzip_ or _bunzip2_.
For example,
```
bzcat gcc-BASEVER.tar.bz2 | tar xvf -
```
This will create a new
directory named **gcc-BASEVER** which has all of the pristine sources.

  * Apply the 6809 patch using the _patch_ command.  You need
to be in the newly created directory, and you need to use the -p1 option to patch:

```
cd gcc-BASEVER
patch -p1 < /path/to/gcc-VERSION.patch
```

You'll see a few messages saying that some files are added/modified.
You should not see any conflicts or errors.

@end enumerate

## Building the Compiler ##

Once the patch is installed, you're ready to build the compiler.

Building a cross-compiler can be a daunting task.  To aid with this, the patch includes a simple Makefile with some basic command sequences for doing the most common things.  This Makefile is installed in the @file{build-6809} subdirectory.

The easiest way to build and install GCC6809 is to switch to this directory and run @command{make}. In most cases, this should be all you need.