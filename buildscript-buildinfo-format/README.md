# buildscript-buildinfo format
This format splits buildscript into to separate files: a .buildscript file and a .buildinfo file. The files server the following two distinct purposes:

## iproute2.buildinfo
Sets various package specific variables (such as the package name) and contains a function called `build`. The `build` function should run the commands necessary to build the actual package, starting with extracting the source tarball and ending immediately before compressing the package into a *.txz file with makepkg.

## iproute2.buildscript
This is effectively a driver for .buildinfo files. It sources the .buildinfo file and uses the variables and functions defined in there to facilitate building the package.

It also allows for different tasks to be done depending on what the first argument to the script is. It supports the following arguments:
* download - Downloads the source tarballs and other source files from the upstream provider.
* verify - Verifies the checksums/signatures of the downloaded source tarballs and files.
* no argument|build - Builds the package, accepting the same variables that the original buildscript format did.

This file should be the same for every single package. This allows us to make global package changes by editing this one file.

