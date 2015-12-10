---
title:  "Compiling cloudy"
date:   2015-12-08
description: Compiling the Cloudy code on a Mac 
---

For future reference...

As documented on the wiki (http://www.nublado.org/wiki/CompilingCloudyOSX) 
Cloudy does not work with current versions of Mac's Xcode c++ compiler. The issue is the 
way it handles floating point exceptions. I currently 
have OS 10.11 (El Capitan) and version 7.1.1 of Xcode.

The workaround suggested on the wiki did work for me. I had to install gcc myself, 
which I did using Homebrew. The first version I tried (4-8) didn't work, but when I built the most 
recent version from source, it fixed things.

brew reinstall --build-from-source gcc

Make sure that this is the version of gcc that gets called when you compile (do "which gcc"), 
and create the appropriate aliases in /usr/local/bin (and update your path) if necessary. 
Homebrew installs everything to /usr/local/.

Once Cloudy is compiled ("make" in the source directory), we can run the programs that are included 
with Cloudy. The easiest way to do this is to run the script "runall.pl" included in the 
programs directory. This script compiles and runs each of the programs listed in the 
"programs.dat" file.

To compile a single sample program (e.g. hazy_coolingcurve) do:

``g++ -ansi -O3 -ftrapping-math -fno-math-errno  -Wall -W -g hazy_coolingcurve.cpp -o hazy_coolingcurve.exe -I../../../source -L../../../source/ -lcloudy``

The following plot is produced with the default settings from the 
hazy_coolingcurve program (solar abundance, $$n_h = 1 \, \mathrm{cm}^{-3}$$).
<img src="{{ site.url }}assets/images/hazy_coolingcurve.png">
