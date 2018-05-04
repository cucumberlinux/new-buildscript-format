# new-buildscript-format
This repository contains various contenders for the new buildscript format for Cucumber Linux 2.0 and the Ports Tree 2.0. Each subdirectory contains an example for one potential format. Eventually, we will review all of the proposed formats and decide which one we want to use as the new official format.

If you have an idea in mind for a format, please feel free to write a prototype for your format and then send us a pull request.

Note: the original-format directory contains an example in the original format; it is not a contender.

## Why a new buildscript format?
The original buildscript format was heavily inspired by the Slackware .SlackBuild format. This allowed for the entire buildscript to be locaed in a single file that could be run on its own, without the presence of a build infrastructure. While this is convenient, it has started to become a little unmanagable for the following reasons:
* It doesn't use any form of templates. This means it is not possible to make any sort of global change without manually editing every single buildscript.
* It doesn't sufficiently track information about the package's upstream. For exmple, it would be very helpful if the build system could track:
  * What the upstream URL is for a project.
  * What the signature/checksum of the source tarball it.
  * What PGP keys are valid for signing each package.

