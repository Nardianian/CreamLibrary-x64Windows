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
