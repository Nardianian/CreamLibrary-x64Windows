Before building Cream you should create the pkg search tool file "pd.pc" on your main Pure Data installation folder and the library file "libpd.dll.a" on his "bin" sub-folder.

To create the "pd.pc" file, open a text file and paste this content: "prefix=<your\PureData\path> exec_prefix=${prefix} libdir=${prefix}/bin includedir=${prefix}/src Name: Pure Data Description: Pure Data core headers and libraries Version: 0.56 Libs: L${libdir} -lpd Cflags: -I${includedir}", then export it with the "save as" option by writing both the name and the extension "pd.pc" and indicating "all files" as the extension, choose UTF-8 without BOM as the encoding and as Line endings: LF (not CRLF), if your editor (e.g. Notepad) does not allow saving with CRLF, you can convert it to LF using MSYS2:
   -  dos2unix /c/PureData/pd.pc
 After this, the file will be readable correctly by pkg-config . To check from Mingw64 run:
   -  pkg-config --cflags --libs pd

To create the static library "libpd.dll.a" for MinGW you can easily derive it from "pd.dll" with the MSYS2 binutils tools, from Mingw64 run:
   -  cd /c/PureData/bin gendef pd.dll dlltool -d pd.def -l libpd.dll.a -D pd.dll
 Now in the PureData\bin folder you will have:
   -  pd.dll
   -  pd.lib      (MSVC import lib (not used by MinGW)    
   -  libpd.dll.a (import lib for gcc).
