## About this fork
Cream Library is a library of externals for Pure Data developed 10 years ago by the CICM team (Centre de recherche en informatique et création musica of the Musidanse department of the University of Paris 8) 
  - [https://musidanse.univ-paris8.fr/centre-de-recherche-en-informatique-et-creation-musicale-cicm?lang=fr]

developers Pierre Guillot, Eliott Paris, Julien Colafrancesco.

The library is also useful if not necessary for using the HOA externals spatialization library dating back to around 2015 but perhaps some more recent updates can be found online
  - [https://cicm.univ-paris8.fr/index.html]

This CreamLibrary fork starts from Timothy Beyer's fork, which 3 years ago updated some parts of the code, to make it fully compatible with Windows x64.

 Included in the repo are both the final dll of the external ready for PD and the static library with the .a extension of CicmWrapper ready to be linked to the Cream code if you want to build it but if you want to compile from source code it is recommended to redo the build of CicmWrapper too (you should get "libCicmWrapper.a").
 Make sure libCicmWrapper.a is visible to the linker. You can pass the paths in Mingw64 runnin' like this:
 
 -  export LDFLAGS="-L/c/Users/capoc/Repos/CreamLibrary/ThirdParty/CicmWrapper" export
 -  CPPFLAGS="-I/c/Users/capoc/Repos/CreamLibrary/ThirdParty/CicmWrapper/Sources"
 
 Then do the build

 The build was conducted on Windows 11 Home with Pure Data v0.56.1 and MSYS2 MINGW64.
Some adjustments have been made to the original source code to bring it from Win32 to x64 (e.g. replaced long with intptr_t ; for Casting pointers to int used intptr_t or uintptr_t from <stdin t.h>), on "eclass.c" from CicmWrapper code was added to the top of the file << #include "m_pd.h" >> and << #include <stdint.h> >>, rewritten the "Makefile.am" files both Cream and CicmWrapper, etc...).  
 In MSYS2 MINGW64 make sure you have:
  - pacman -Syu # upgrade MSYS2 pacman -S base-devel
  - pacman -Syu pacman -S autoconf automake libtool m4 pkgconf make gcc
  - pacman -S mingw-w64-x86_64-toolchain pacman -S pkg-config # useful for pd

Build CicmWrapper first, then build "libpd.dll.a" on your PureData\bin folder and make sure to link Cream to "libCicmWrapper.a" with the correct directory, then when building both CicmWrapper (static) and Cream (force it to dynamic with < --enable-shared --disable-static >) always on MSYS2 MINGW64 communicate the correct directories of your Pure Data installation path, eg.
To build CicmWrapper:
  -  ./autogen.sh ./configure --with-pd=</c/your-PureData-install-path> make
To build Cream:
  -  make clean  ./autogen.sh ./configure --with-pd=</c/your-path-to-PureData> --with-extension=dll --enable-shared --disable-static make

Check the correspondence with your directories in the files, in particular in the "Makefile.am" and "configure.ac"

# Original Readme:

## [Cream Library](http://www.mshparisnord.fr/hoalibrary/en/publications/ "Publication") for Pure Data

A set of PD externals for those who like vanilla... but also want some chocolate cream.  
The Cream Library uses the [CICM Wrapper](https://github.com/CICM/CicmWrapper" "CICM Wrapper") developed to facilitate the creation of signal objects and GUI and to improve user interactions to offer a set of externals that improve the user interaction in Pure Data.

### Compatibility:

The latest release has been tested on [Pure Data Vanilla](http://msp.ucsd.edu/software.html "PD-Vanilla") (0.52.2 - 64 bit) on FreeBSD.  

It should also work on older versions such as 0.46.6, on [Pure Data Extended](https://puredata.info/ "PD-Extended") (0.43.4), and also on Linux, Mac OS, and Windows, in 32 or 64-bit, as it did in the past.

### Installation:

With Pure Data Vanilla, copy the <em>Cream</em> folder in your package folder and add <em>Cream</em> in PD's startup window if you use the default package folder\*, otherwise add <em>Cream/Cream</em>.  

With Pure Data Extended, copy the <em>Cream</em> folder in your package folder and add <em>-lib externals/Cream</em> in the startup flags if you use the default package folder\*, otherwise add <em>-lib Cream/Cream</em>.  

\* The default package folder are generally <em>/usr/local/lib/pd-externals</em> on Linux, <em>/Library/Pd</em>  on Mac Os and <em>C:\Program Files\Common Files\Pd</em>  on Windows.

### Documentation:

Help and tutorials are available in the <em>Cream</em> folder of the <em>help browser</em>.

### Compilation:

	./autogen.sh (if needed)
	./configure (useful options --with-pd=</path/to/pd>)
	make
	make install (optional)

XCode, Code::Blocks and Visual Studio projects are also available.

### Dependencies:

[Cicm Wrapper](https://github.com/CICM/CicmWrapper "Cicm Wrapper").

### Authors:

Pierre Guillot  

### License:

Copyright (C) 2013-2015 Pierre Guillot - CICM - Universite Paris 8  
The Cream Library in under the [BSD2 License](http://opensource.org/licenses/BSD-2-Clause "BSD2").
