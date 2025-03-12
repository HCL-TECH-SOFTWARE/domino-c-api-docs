##### Chapter 1-4
##### Software Compatibility

<b><font size="5" color="#000080">Platforms and Compilers</font></b><br>
<br>
This section identifies the compilers and tools you can use to develop C API programs on each supported platform.<br>
<br>
Programs created with the HCL C API Toolkit for Notes/Domino 14.5 run under HCL Domino or HCL Notes 14.5 or later. They do not run under earlier releases of Domino or Notes.<br>
<br>
<b><font size="4" color="#000080">Microsoft Windows </font></b><br>
<br>
You can develop 32-bit programs for all supported Windows 32-bit platforms using Microsoft Visual Studio 2010. <br>
<br>
You can develop 64-bit programs for all supported Windows 64-bit platforms using Microsoft Visual Studio 2017. <br>
<br>
<b><font size="4" color="#000080">Linux</font></b><br>
<br>
<br>
You can develop programs for Linux 64bit using RHEL and the GNU Compiler Collection (gcc) version 4.8.x.  These applications can also be run on SuSE Linux.<br>
<br>
<br>
<b><font size="4" color="#000080">AIX</font></b><br>
<br>
You can develop programs for AIX using XLC/XLC++ 13 compiler for C-API toolkit earlier to V14. For V14, supported version is XLC/XLC++ 16.1 compiler.<br>
<br>
<b>Building New C API Applications with the libnotes_r.a Library</b><br>
<br>
1/19/21 - this may be outdated information but keeping it just in case - Note that there are two different crt0_r.o files, /usr/ccs/lib/crt0_r.o and /usr/lpp/xlC/lib/crt0_r.o. If you link with the second file, the application links but throws a segmentation error during its execution. Therefore, you should specify the path to the crt0_r.o file explicitly:<br>
<br>
<tt>/usr/lib/crt0_r.o</tt> 	(which is linked to /usr/ccs/lib/crt0_r.o)<br>
  	<br>
Also note that there may be linker warning (duplicate symbol) messages during the command execution.<br>
<br>
<br>
<br>
<b><font size="4" color="#000080">IBM i</font></b><br>
<br>
You can also develop programs for IBM i - see User Guide Chapter 3-3 Building IBM i Applications.  To build IBM i applications, you also need to install the HCL C API Toolkit for Notes/Domino for IBM i.<br>
<br>
<br>
<b><font size="4" color="#000080">Running C API Applications with the New Releases of Domino on UNIX</font></b><br>
<br>
Any UNIX compiler stores in the executable the original  full path name of the Domino shared library.  If the recommended path link to the Domino executable directory <br>
	(<tt>/opt/lotus/notes/</tt><tt><b>latest</b></tt><tt>/arch</tt>) <br>
was used, the application follows the link. Otherwise, the application crashes at runtime. To avoid this, a developer should either use this link at the time when the application is created, or require that the following variables include the Domino executable directory at run time:<br>
<br>
for AIX: 		<tt>LIBPATH</tt><br>
for Linux:	<tt>LD_LIBRARY_PATH</tt><br>
<br>
<br>
<br>
<b><font size="5" color="#000080">Previously Built Notes C API Programs Running on Domino or Notes 14.5 and later</font></b><br>
<br>
Generally, C programs created with previous versions of the Notes C API Release will run under both HCL Domino and HCL Notes Release 14.5.  See the Known Problems, Corrections, and Additions chapter in this <i>User Guide </i>for exceptions.<br>
<br>
<br>
<b><font size="5" color="#000080">Rebuilding Programs Created with Earlier Releases of the Notes C API </font></b><br>
<br>
If you use the HCL C API for Notes/Domino 14.5. to recompile a program you created with an earlier version of the C API, the program will not work on Domino or Notes Releases prior to Notes/Domino 14.5.<br>
<br>
<b><font size="4" color="#000080">Source Code Compatibility</font></b><br>
<br>
Source code created with previous versions of the C API may require some modifications to compile correctly with the current version of the HCL C API for Notes/Domino. These changes are explained in the &quot;Migration Issues&quot; and &quot;Changes to Release ...&quot; chapters in this guide and are illustrated in the sample programs.  <br>
<br>
<br>
<b><font size="5" color="#000080">Database Compatibility</font></b><br>
<br>
A C API program running under a previous Notes Release can access databases on a server running HCL Domino 14.5. The databases on the HCL Domino 14.5 server can have previous Domino database properties.<br>
<br>
A C API program  running under Domino or Notes 14.5 can access databases on a older server running HCL Domino.<br>
<br>
NOTE: When you use older versions of Notes  to access a HCL Domino 14.5  database, you must perform that access through HCL Domino 14.5 or later release.   Do not copy a HCL Domino 14.5 database directly to a machine running a previous version of HCL Domino or Notes. The older Domino software will not be able to read this database.
---
