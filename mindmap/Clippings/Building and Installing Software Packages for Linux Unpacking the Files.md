---
title: "Building and Installing Software Packages for Linux: Unpacking the Files"
source: "https://tldp.org/HOWTO/Software-Building-HOWTO-2.html"
author:
published:
created: 2025-05-11
description:
tags:
  - "clippings"
---
[Next](https://tldp.org/HOWTO/Software-Building-HOWTO-3.html) [Previous](https://tldp.org/HOWTO/Software-Building-HOWTO-1.html)

---

## 2\. Unpacking the Files

You have downloaded or otherwise acquired a software package. Most likely it is archived (*tarred*) and compressed (*gzipped*), in `.tar.gz` or `.tgz` form (familiarly known as a "tarball"). First copy it to a working directory. Then *untar* and *gunzip* it. The appropriate command for this is **tar xzvf *filename***, where *filename* is the name of the software file, of course. The de-archiving process will usually install the appropriate files in subdirectories it will create. Note that if the package name has a *.Z* suffix, then the above procedure will serve just as well, though running **uncompress**, followed by a **tar xvf** also works. You may preview this process by a **tar tzvf filename**, which lists the files in the archive without actually unpacking them.

The above method of unpacking "tarballs" is equivalent to either of the following:

- gzip -cd filename | tar xvf -
- gunzip -c filename | tar xvf -
(The '-' causes the *tar* command to take its input from `stdin`.)

Source files in the new *bzip2* (`.bz2`) format can be unarchived by a **bzip2 -cd filename | tar xvf -**, or, more simply by a **tar xyvf filename**, assuming that `tar` has been appropriately patched (refer to the [Bzip2 HOWTO](https://metalab.unc.edu/pub/Linux/docs/HOWTO/mini/Bzip) for details). Debian Linux uses a different patch for `tar`, one written by Hiroshi Takekawa, so that the *\-I, --bzip2, --bunzip2* options work with that particular `tar` version.

\[Many thanks to R. Brock Lynn and Fabrizio Stefani for corrections and updates on the above information.\]

Sometimes the archived file must be untarred and installed from the user's home directory, or perhaps in a certain other directory, such as `/`, `/usr/src`, or `/opt`, as specified in the package's config info. Should you get an error message attempting to untar it, this may be the reason. Read the package docs, especially the `README` and/or `Install` files, if present, and edit the config files and/or `Makefiles` as necessary, consistent with the installation instructions. Note that you would **not** ordinarily alter the `Imake` file, since this could have unforseen consequences. Most software packages permit automating this process by running **make install** to emplace the binaries in the appropriate system areas.

- You might encounter `shar` files, or *shell archives*, especially in the source code newsgroups on the Internet. These remain in use because they are readable to humans, and this permits newsgroup moderators to sort through them and reject unsuitable ones. They may be unpacked by the **unshar filename.shar** command. Otherwise the procedure for dealing with them is the same as for "tarballs".
- Some source archives have been processed using nonstandard DOS, Mac, or even Amiga compression utilities such *zip*, *arc*,*lha*, *arj*, *zoo*, *rar*, and *shk*. Fortunately, [Sunsite](http://metalab.unc.edu/) and other places have Linux uncompression utilities that can deal with most or all of these.

Occasionally, you may need to update or incorporate bug fixes into the unarchived source files using a `patch` or `diff` file that lists the changes. The doc files and/or `README` file will inform you should this be the case. The normal syntax for invoking Larry Wall's powerful *patch* utility is **patch < patchfile**.

You may now proceed to the build stage of the process.

---

[Next](https://tldp.org/HOWTO/Software-Building-HOWTO-3.html) [Previous](https://tldp.org/HOWTO/Software-Building-HOWTO-1.html)
