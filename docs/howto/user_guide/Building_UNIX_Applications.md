##### Chapter 3-2
##### Building UNIX Applications

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
This chapter identifies the hardware and software requirements for developing HCL C API programs for Domino under UNIX and explains how to set up your UNIX environment. It covers the following topics:<br>
<br>
<b>Getting Started</b><br>
Hardware and software requirements, Compiler installation, Environment settings for compiling the sample, Running HCL C API programs, and Testing the installation<br>
<br>
<b>Program Structure</b><br>
Initialization and file-naming conventions<br>
<br>
<b>Toolkit Files</b><br>
Platform-specific files supplied with the HCL C API Toolkit for Domino<br>
<br>
<b>Compatibility</b><br>
Information on addressing, calling conventions, and data alignment<br>
<br>
<b>Compiling, Linking, Building shared libraries, and Debugging</b><br>
Platform-specific information on compiler, linker, and debugger settings for C API applications<br>
<br>
<b>Porting HCL C API Programs for Domino to UNIX from Windows</b><br>
Specific considerations when porting existing applications to run on UNIX systems<br>
<br>
In addition to the information in this chapter, the chapter on Domino Canonical Format contains important considerations for developing C API applications for UNIX systems<br>
<br>
<br>
<b><font size="5" color="#000080">Getting Started</font></b><br>
<br>
This section describes the hardware and software requirements for each UNIX platform supported by the HCL C API for Domino.<br>
<br>
<br>
<b><font size="4" color="#000080">Hardware and software requirements</font></b><br>
<b><font color="#000080"> </font></b><br>
Same Hardware requirements as those noted for the Domino server with addition of space to afford room for C API toolkit and compilation.  Minimum software requirements are used for the build environment (for example, if Domino supports Linux version 7 and 8, then 7 is the build platform as you must always build on the lowest supported OS level)<br>
<br>
<b><font size="4" color="#000080">Compiler installation</font></b><br>
<br>
There are no special requirements for installation of the compilers or other tools. <br>
<br>
<br>
<b><font size="4" color="#000080">Environment settings for compiling the sample</font></b><br>
<br>
This section explains how to set up your UNIX environment to build and run HCL C API programs for Domino. <br>
<br>
<b><font color="#000080"> Summary</font></b><br>

<ul type="disc">
<li>Make sure HCL Domino and the HCL C API for Domino are installed.
<li>Set the environment variable LOTUS to the canonical Lotus directory, /opt/hcl, if necessary. All HCL software is installed in the canonical Lotus directory.
<li>While developing HCL C API programs for Domino, set the environment variable Notes_ExecDirectory to specify the Domino executable directory. </ul>
<br>
The sections that follow define the following concepts:<br>

<ul type="disc">
<li>The canonical Lotus directory 
<li>The Domino executable directory</ul>
<br>
<br>
<b><font color="#000080"> The canonical Lotus directory</font></b><br>
<br>
The canonical Lotus directory is the directory in which all Lotus products for UNIX are installed.  A canonical Lotus directory is required because on some UNIX systems shared libraries are found in absolute file system locations.<br>
<br>
Set the environment variable <tt><b>LOTUS</b></tt> to point to this directory:<br>

<ul type="disc">
<li><tt>/opt/hcl </tt>				for all UNIX platforms</ul>
<br>
If you use the C shell, your .cshrc file should contain the line:<br>
<br>
<tt>setenv LOTUS /opt/hcl		</tt>	for all UNIX platforms<br>
<br>
        For sh or ksh,  your initialization file should contain the following:<br>
<br>
<tt>LOTUS=/opt/hcl; export LOTUS	</tt>for all UNIX platforms<br>
<br>
All Domino and Notes Client software should be installed in the canonical Lotus directory. Specifically,<br>

<ul type="disc">
<li>The Domino program directories should reside in $LOTUS/notes. 
<li>The HCL C API Toolkit for Domino and Notes should reside in $LOTUS/notesapi.</ul>
<br>
All UNIX platforms support symbolic directory links. Therefore, Lotus products may physically reside anywhere in the file system, so long as a directory link in the canonical Lotus directory points to where the product actually resides. For example, the directory /opt/hcl/notesapi may be a symbolic link to the directory where the HCL C API Toolkit for Domino and Notes physically resides. <br>
<br>
The make files for HCL C API sample programs for Domino and Notes use $LOTUS to locate the directory where the HCL C API for Domino and Notes include files and object files reside. <br>
<br>
<br>
<b><font color="#000080"> The Domino executable directory</font></b><br>
<br>
The Domino executable directory is the directory where the Domino executable program libraries reside. Relative to $LOTUS, the root of the Lotus tree, the Domino executable directory is:<br>
<br>
<tt>$LOTUS/notes/</tt><i><font face="Times New Roman">latest</font></i><tt>/</tt><i><font face="Times New Roman">arch</font></i><br>
<br>
<br>
Where<br>
<br>
<b><i><font face="Times New Roman">latest</font></i></b> is a symbolic link to the release name (for example, <b>110001</b>), <br>
<br>
<b><i><font face="Times New Roman">arch</font></i></b><b> </b>is the code name for the architecture of the UNIX platform (for example, <b>ibmpow</b>).  It consists of up to three letters for the vendor (for example<b>, </b><b>ibm</b>) and up to three letters for the CPU or machine type (for example, pow for POWER). For example, the Domino executable directory for Domino for IBM AIX Edition is:<br>
<br>
<tt>$LOTUS/notes/latest/ibmpow</tt><br>
<br>
<br>
<br>
By convention, set the environment variable <tt><b>Notes_ExecDirectory</b></tt> to point to the Domino executable directory. If you use the C shell, your .cshrc file should contain the line:<br>
<br>
<tt>setenv Notes_ExecDirectory your-Domino-executable-directory</tt><br>
	 <br>
        For sh or ksh,  your initialization file should contain the following:<br>
<br>
<tt>Notes_ExecDirectory=your-Domino-executable-directory; </tt><br>
<tt>export Notes_ExecDirectory</tt><br>
<br>
<br>
<br>
<b><font size="4" color="#000080">Running HCL C API programs</font></b><br>
<br>
This section explains how to set up your UNIX environment to run HCL C API programs for Domino.<br>

<p>Change the C API program with the owner, group, and file permission. Install the C API program executable file into the Domino executable directory, then create a sym link of tools/startup in $LOTUS/bin. For example,
<p>% cp apiprog $LOTUS/notes/latest/ibmpow/apiprog
<p>% cd $LOTUS/bin
<p>% ln -s tools/startup apiprog
<p>
<p>Change to the Domino data directory and start the C API program. For example,
<p>% cd /local/notesdata
<p>% /opt/hcl/bin/apiprog
<p>
<p><b><font color="#000080"> Owner, group, and file permissions</font></b><br>
<br>
UNIX is a Domino Server only platform.  It is required that you run C API programs on UNIX under the same login as the server.<br>
<br>
After compiling but before running a HCL C API program for Domino, make sure the executable file for the C API program has the same owner and group as other Domino binaries and also has the set group-id bit set.<br>
<br>
By default, all Domino executable files have owner &quot;root&quot; and group &quot;system&quot; For example, a command to list the owner, group, and permissions of the Domino executable &quot;server&quot; for Domino for AIX would print something similar to the following:<br>
<br>
<tt>% ls -l $LOTUS/notes/latest/ibmpow/server</tt><br>
<tt>-rwxr-xr-x 1 root system 14102624 June 25, 06:39 /opt/hcl/notes/latest/ibmpow/server</tt><br>
<br>
In this case, you must set the owner of your C API executable program to &quot;root&quot; and the group  to &quot;notes&quot;, The following commands show how to set the owner, group, and permissions of the C API sample program executable &quot;intro&quot; to the required values:<br>
<br>
<tt>% cd $LOTUS/notesapi/samples/basic/intro</tt><br>
<tt>% su</tt><br>
<tt>Password: </tt>&lt;enter the super user password&gt;<br>
<tt># chown root intro</tt><br>
<tt># chgrp system intro</tt><br>
<tt># chmod 2555 intro</tt><br>
<tt># exit</tt><br>
<tt>%</tt><br>
<b><font color="#000080">The Domino data directory</font></b><br>
<br>
The Domino data directory is the directory containing server's notes.ini file, the Domino databases, and templates. <br>
<br>
Under UNIX, the default Domino data directory is named <tt><b>/local/notesdata</b></tt> and it must reside on the local disk.<br>
<br>
<b><font color="#000080">The initialization algorithm</font></b><br>
<br>
When you invoke a program via /opt/hcl/bin/FOO it invokes our startup script which sets up the environment so that we can find our executables as well as our resources files required for Domino to run.  This means that as long as you put your binary in /opt/hcl/notes/latest/ARCH and make the correct symbolic link as noted above then your executable will run fine.  If you wish to locate your binary elsewhere, then you can use the startup script to directly invoke your executable and we will still be able to find our libraries and resource files.  This is done with the syntax:  /opt/hcl/notes/latest/ARCH/startup /full_path_to_my_executable/my_executable<br>
<br>
<b><font size="4" color="#000080">Testing the installation</font></b><br>
<br>
After installing Domino, the C compiler, the development files, the documentation, and the sample C API programs, follow these steps to build and test the sample C API program<i> </i><b><i>intro</i></b>. Any problem building or executing an unmodified sample program indicates a problem in the environment.<br>

<ol type="1">
<li>Verify that Domino for UNIX executes successfully in your environment. C API programs require that Domino is installed properly in the environment.<br>

<li>Open an xterm window, or use rlogin or telnet to get a shell and a command prompt.<br>

<li>Copy all the files under the<b> intro</b> directory to a directory under your home directory. Under the default installation of the HCL C API Toolkit for Domino and Notes, this sample directory is located under:<br>
<br>
/opt/hcl/notesapi/samples/basic/intro<br>

<li>Change to the directory where <tt><b>intro</b></tt> was copied and type <tt><b>ls</b></tt> to list the files in this directory. <br>
 <br>
The .mak files in this directory are make files for the various operating environments. The C API kit includes multiple build support files for samples that can be built for multiple platforms.<br>

<li>Build <tt><b>intro</b></tt> using the make file appropriate to your operating environment. For example, if you are developing on a  Linux system, type the following command at the command prompt: <br>
<br>
<tt>make -f linux.mak<br>
<br>
</tt>The program should compile and link with no errors.<br>

<li>Copy the database,<tt><b>&nbsp;intro.nsf</b></tt>, from the <tt><b>notedata</b></tt> directory in the C API kit to the Domino data directory.  Under the default installation of the HCL C API Toolkit for Domino, this database is located under:<br>
<br>
/opt/hcl/notesapi/notedata/intro.nsf<br>

<li>Enter this at the command prompt:<br>
<br>
<tt>intro intro.nsf<br>
<br>
</tt>It should display the HCL C API for Domino and Notes release number followed by:<br>
<br>
<tt>The title for the database intro.nsf is...<br>
<br>
API Test Database (intro)<br>
<br>
</tt>
<li>Start Notes on a client machine. Open the database &quot;<b>intro.nsf</b>&quot; on the UNIX server. <br>

<li>Check the database title by selecting File - Database - Properties. The title should be the same as the one printed by the<tt>&nbsp;intro</tt>  sample: &quot;API Test Database (intro).&quot;<br>
<br>
</ol>
<br>
<b><font size="5" color="#000080">Program Structure</font></b><br>
<br>
<b><font size="4" color="#000080">Program Initialization</font></b><br>
<br>
C API programs for UNIX may use any of the following methods to initialize the Domino or Notes Client run-time system.<br>
<br>
<b><font color="#000080">NotesMain</font></b><br>
<br>
You can structure C API programs for UNIX as a subroutine named NotesMain. In this case, link with the bootstrap object file notes0.o. This object file provides the &quot;main&quot; program required by UNIX systems.<br>
<br>
NotesMain uses the system's standard calling convention. The argument count provided to the subroutine is an integer.<br>
<br>
<br>
<b><font color="#000080">AddInMain</font></b><br>
<br>
HCL Domino Server add-in tasks are usually structured as a subroutine named AddInMain. This type of program must be linked with both platform-specific bootstrap object files notes0.o and notesai0.o. These object files provide the &quot;main&quot; program and perform server add-in initialization.<br>
<br>
Like NotesMain, AddInMain uses the system's standard calling convention. The argument count provided to the subroutine is an integer.<br>
<br>
<br>
<b><font color="#000080">main</font></b><br>
<br>
You can structure the program as a standard C or C++ program with entry point main. In this case, the program must call the function NotesInitExtended to explicitly initialize the Domino run time system before calling any other HCL C API for Domino and Notes functions. When the program no longer needs to call any HCL C API functions for Domino and Notes, it must call the function NotesTerm to terminate the Domino run time system explicitly.<br>
<br>
<b><font color="#000080">MainEntryPoint</font></b><br>
<br>
You can structure the program as a shared object library with a main entry point named MainEntryPoint. In this case, the C API program is configured as an add-in to the software. Typically, the Notes client or Domino server software loads and calls the main entry point of this custom library in response to a Notes user's command or menu selection. In this case, the Domino run-time system is initialized before MainEntryPoint receives control. The Domino or Notes run-time system is terminated when the user exits Domino or Notes.<br>
<br>
Under the LINUX environment the function definition of MainEntryPoint must use extern &quot;C&quot;.  This will prevent MainEntryPoint from being mangled.  For further information please reference the &quot;gcc/g++&quot; online reference.<br>
<br>
<br>
<b><font size="4" color="#000080">Naming Conventions</font></b><br>
<br>
<b><font color="#000080">Platform-Specific File Directories</font></b><br>
<br>
The platform-specific files supplied with the HCL C API Toolkit for Domino and Notes are in the library directory. The pathname for this directory depends on the platform:<br>
<br>
AIX:	$LOTUS/notesapi/lib/aix<br>
Linux:	$LOTUS/notesapi/lib/linux<br>
<br>
<br>
<br>
<b><font color="#000080">Custom Libraries</font></b><br>
<br>
Under Windows, custom libraries such as extension managers are in the form of dynamic link libraries (DLLs). Under UNIX, custom libraries are in the form of shared objects.<br>
<br>
On all UNIX platforms, the filenames of shared objects must start with the characters &quot;lib&quot;. Append to &quot;lib&quot; the name you want to give the file, followed by a platform-specific extension. The extensions used by the various UNIX platforms are as follows:<br>
<br>
<u>Platform</u>	<u>File extension</u>	<u>Typical Filename</u><br>
AIX	.a		libfoo_r.a<br>
Linux	            .so			libfoo.so<br>
<br>
<br>
<b><font size="5" color="#000080">Toolkit Files</font></b><br>
<br>
This section describes the components of the HCL C API Toolkit for Domino and Notes that support building applications for UNIX  platforms.<br>
<br>
<br>
<b><font size="4" color="#000080">HCL C API Header Files for Domino</font></b><br>
<br>
In the HCL C API Toolkit for Domino, support for all platforms is provided by the common include files in $LOTUS/notesapi/include. When compiling, the Domino header files require the use of the many compiler command-line switches which will be detailed below and are also in the PLAT_cmp.txt file included in the include directory of the SDK. For details, see &quot;Compiling,&quot; below.<br>
<br>
Be aware that the UNIX platform ID macro, &quot;-DUNIX&quot; also defines the W32 platform ID macro which stands for the Win32 APIs. If you need conditional compilation for 32-bit Windows, but not for UNIX, be sure to check that W32 is defined and UNIX is not defined, Alternatively you can use the NT platform ID macro for 32-bit Windows conditional compilation. There are 32 and 64 bit specific defines as well - please see the PLAT_cmp.txt or below for more info.<br>
<br>
<b><font color="#000080">Header File Conflict</font></b><br>
<br>
It is possible that a header file that is included with the compiler's software development kit may have the same name, but different contents, as a C API for Domino and Notes header file. If your API program requires the HCL C API header file for Domino and Notes but does not require the other file that has the same name, you may resolve the conflict including the HCL C API for Domino and Notes headers before the others during compilation. Alternatively, you may specify the full path of the header file in the #include statement in your source code. This alternative allows your program to include both files in a single source module.<br>
<br>
It is also possible that a header file that is included with the compiler's software development kit may contain a definition that is also defined in a header file in the HCL C API Toolkit for Domino and the syntax of the definitions cause errors when compiling source code that includes both header files.  In such cases it is recommended to keep code that requires each header file in a separate module.<br>
<br>
<br>
<b><font size="4" color="#000080">HCL C API Library Files for Domino</font></b><br>
<br>
Since the HCL C API for Domino is supplied as a shared object library on UNIX platforms, no separate library files are supplied with the HCL C API Toolkit for Domino and Notes. For details, see &quot;Linking,&quot; below.<br>
<br>
<br>
<b><font size="4" color="#000080">HCL C API Bootstrap Object Files for Domino</font></b><br>
<br>
The bootstrap object files in the platform-specific subdirectories under $LOTUS/notesapi/lib are required to construct  C API programs using the NotesMain entry point and to construct server add-in tasks. The file notes0.o provides the entry point and Domino run-time initialization for Domino applications. The file notesai0.o is used in conjunction with notes0.o to provide the entry point and run-time initialization for HCL Domino Server add-in tasks.<br>
<br>
<br>
<b><font size="5" color="#000080">Compatibility</font></b><br>
<br>
<b><font size="4" color="#000080">Data Structure Packing</font></b><br>
<br>
On UNIX systems, most data structures passed between Domino and API applications are aligned on the appropriate data boundaries. However, some structures containing data that is stored directly in a Domino database are stored in Domino canonical format. You must convert this data using ODSReadMemory and ODSWriteMemory. For more information, see the &quot;Domino Canonical Format&quot; chapter.<br>
<br>
<br>
<b><font size="4" color="#000080">Features Not Supported by Domino for UNIX</font></b><br>
<br>
The following features of C API programs are not supported under UNIX due to design limitations in Domino:<br>

<ul type="disc">
<li>Notes client menu add-ins</ul>
	These are executable program libraries loaded and called by Notes when the user selects custom items from the File -Tools menu.<br>

<ul type="disc">
<li>API programs such as IMPORTER</ul>
	These are programs that load and call import/export libraries provided by Notes.<br>

<ul type="disc">
<li>Notes/FX (Field Exchange)</ul>
	This feature is only supported under Windows.<br>
<br>
<br>
<b><font size="5" color="#000080">Compiling</font></b><br>
<br>
<b><font size="4" color="#000080">Platform ID Macro</font></b><br>
<br>
UNIX platforms require two macros. All UNIX platforms require the platform ID macro &quot;UNIX&quot;, to distinguish them from PC-based environments. In addition, each UNIX platform has a platform-specific ID macro:<br>
<br>
AIX64:	AIX<br>
	AIX64<br>
<br>
Linux64:	LINUX<br>
	LINUX64<br>
<br>
<br>
<b><font size="4" color="#000080">Compiler Switches and Options</font></b><br>
<br>
The recommended compiler switches and options depend on the compiler you use.  Please see the platform specific PLAT_cmp.txt files for more info<br>
<br>
<b><u><font color="#000080">Linux64</font></u></b><br>
To compile Domino C API applicaitons under Linux use the switches in linux64_cmp.txt<br>
<br>
<br>
<b><u><font color="#000080">AIX64</font></u></b><br>
To compile C API applications under AIX65, use the switches in aix64_cmp.txt<br>
<br>
<b><font size="5" color="#000080">Linking</font></b><br>
<br>
<b><font size="4" color="#000080">Stack Size</font></b><br>
There are no special considerations for stack size for UNIX C API applications for Domino.<br>
<br>
<b><font size="4" color="#000080">Linker Switches</font></b><br>
The recommended linker switches depend on the linker you use.<br>
<br>
<b><u><font color="#000080">Linux64</font></u></b><br>
To link C API applications under Linux64, use the switches in linux_cmp.txt.<br>
<br>
<b><u><font color="#000080">AIX64</font></u></b><br>
To link executable C API applications under AIX64, use the switches in aix64_cmp.txt<br>
<br>
<br>
<b><font size="5" color="#000080">Building shared libraries</font></b><br>
<br>
<b><font size="4" color="#000080">Linker Switches</font></b><br>
<br>
The recommended linker switches depend on the linker you use.<br>
<br>
<b><u><font color="#000080">Linux64</font></u></b><br>
To link C API applications under Linux, use the switches in linux64_cmp.txt.<br>
<br>
<br>
<b><u><font color="#000080">AIX64</font></u></b><br>
To link executable C API applications under AIX64, use the switches in aix64_cmp.txt:<br>
<br>
<b><font size="5" color="#000080">Debugging</font></b><br>
<br>
To build a version of an application for symbolic debugging, add the following flag to the compiler command:<br>
<br>
	-g	Cause the compiler to generate additional information needed by the symbolic debugger.<br>
<br>
You may want to avoid use of the -O flag, used to generate optimized code.<br>
<br>
<br>
<br>
<b><font size="5" color="#000080">Porting HCL C API Programs for Domino to UNIX from Windows</font></b><br>
<br>
Follow these steps to port your existing C API programs from Windows to UNIX.<br>
<br>
<b><font size="4" color="#000080">Step 1: Avoid Features That Are Only Supported under Windows</font></b><br>
<br>
Make sure your API program does not use any of the features listed in &quot;Features Not Supported by Notes for UNIX&quot; above. If it does, consider alternative solutions.<br>
<br>
<br>
<b><font size="4" color="#000080">Step 2:</font></b><font size="4" color="#000080"> </font><b><font size="4" color="#000080">Port Platform-Specific Code</font></b><br>
<br>
Since most HCL C API functions for Domino and Notes are portable, most of the platform-specific code in a typical application appears in the system calls and the user interface.<br>
<br>
Place portable C API code and non-portable system and UI code in separate modules. Define generic wrapper functions in the platform-dependent modules that can be called from the portable modules. Create a new platform-dependent module for each new platform you port to.<font color="#FF0000"> </font>This technique may help you maintain core code used for both the Windows and the UNIX versions of a program.<br>
<br>
To help simplify porting, replace platform-dependent system calls, with standard C run-time functions. <br>
<br>
<br>
<b><font size="4" color="#000080">Step 3: Use NotesInitExtended</font></b><br>
<br>
If your program calls NotesInit (rather than NotesMain or AddinMain), change it to call NotesInitExtended instead. <br>
<br>
<b><font size="4" color="#000080">Step 4: Perform Host/Canonical Conversion via ODS functions as needed</font></b><br>
<br>
Read the &quot;Domino Canonical Format&quot; chapter in this guide. Find the places where your API program reads or writes any of the data types listed below, and modify these sections of your code to perform host/canonical conversion:<br>
<br>
  TYPE_COMPOSITE<br>
  TYPE_COLLATION<br>
  TYPE_OBJECT<br>
  TYPE_VIEW_FORMAT<br>
  TYPE_ICON<br>
  TYPE_SIGNATURE<br>
  TYPE_SEAL<br>
  TYPE_SEALDATA<br>
  TYPE_SEAL_LIST<br>
  TYPE_WORKSHEET_DATA<br>
  TYPE_USERDATA<br>
<br>
This step has the greatest impact on C API programs that access rich text fields directly via the individual CD records. It also affects C API programs that access design notes, such as form, view, or macro notes. It does not affect C API programs that manipulate rich text via the high-level CompoundText* routines.<br>
<br>
For all other data types, the Domino NSF subsystem performs the conversion automatically.<br>
<br>
<br>
<b><font size="4" color="#000080">Step 5: Use Memcpy to avoid Bus Errors</font></b><br>
<br>
Often, code ported to UNIX from Windows crashes at run time with the system error message &quot;Bus Error.&quot; The most common cause is an attempt by a program to access an integral data type at an address that is not a multiple of the data type size, or to access a data structure at an address that is not to a multiple of the size of the data structure's largest simple element.<br>
<br>
To avoid the most common causes of bus errors, find the places where the API program gets a pointer to a data structure from Domino. Use memcpy to copy the data structure into a local variable before accessing its members. Use the local variable, not the pointer provided by Domino, to access the structure members.<br>
<br>
This step has an impact on a wide range of HCL C API programs for Domino. For example, when searching for notes in a database, Domino passes a pointer to a SEARCH_MATCH structure as one of the input arguments to the NSFSearch action routine. This SEARCH_MATCH pointer provided by Domino may not be aligned properly for the SEARCH_MATCH data type, since Domino data frequently resides in packed memory buffers.<br>
<br>
The action routine must call memcpy to copy the SEARCH_MATCH structure from the address specified by the pointer to a local variable of type SEARCH_MATCH. The action routine must only use this local variable, not the pointer, to access the structure members. Using the pointer to access members of the SEARCH_MATCH structure may yield a bus error. See the example below.<br>
<br>
<br>
<b><font color="#000080">Background</font></b><br>
<br>
The reasons for bus errors stem from differences between Intel and RISC processors and compilers. Program code on Intel-architecture platforms can access any data type at any address. On other platforms, C source code that reads a 32-bit quantity, such as a long integer, from a particular memory address, causes the C compiler to emit a 32-bit load instruction. In this case, the memory address must be aligned on a 32-bit (4-byte) boundary. If the memory address is not properly aligned, the hardware will generate an interrupt. The kernel will trap this interrupt and send a BUS ERROR signal to the process running the program.<br>
<br>
Generally, the following rules apply to all UNIX/RISC combinations:<br>

<ol type="1">
<li>Any data type is aligned to an address that is a multiple of its own size.
<li>Any structure is aligned to the strictest alignment of all of its elements (that is, to a multiple of the size of its largest simple element or to the alignment of a contained structure if that is stricter).
<li>Any array of the data type is aligned to the alignment of its elements, and any element in the array is similarly aligned.
<li>Alignment is consistent unless compiler options or pragmas alter it.</ol>
<br>
<br>
<b><font color="#000080">Example</font></b><br>
<br>
The code below shows how part of the sample program nsf_dump was modified to avoid a bus error. The original code caused a bus error at the line that accesses the NoteID member of the SEARCH_MATCH data structure.<br>
<br>
Before porting to UNIX:<br>
<br>
<tt>/************************************************************************</tt><br>
<br>
<tt>&nbsp; FUNCTION: &nbsp;DumpOneNote</tt><br>
<br>
<tt>&nbsp; PURPOSE: &nbsp;This is the action routine specified to NSFSearch</tt><br>
<br>
<tt>&nbsp; INPUTS: &nbsp; void far *Param &nbsp; &nbsp; &nbsp; &nbsp; - not used</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; SEARCH_MATCH far *pSearchMatch - information about the</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;note that was found</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; ITEM_TABLE far *SummaryBuffer &nbsp;- not used</tt><br>
<br>
<tt>*************************************************************************/</tt><br>
<br>
<tt>STATUS LNPUBLIC DumpOneNote( void far * Param,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;SEARCH_MATCH far *pSearchMatch,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ITEM_TABLE far * SummaryBuffer )</tt><br>
<tt>{</tt><br>
<tt>&nbsp; STATUS Error;</tt><br>
<tt>&nbsp; char &nbsp;szClass[LINELENGTH+1];</tt><br>
<tt>&nbsp; DWORD &nbsp;dwDumpCount;</tt><br>
<br>
<tt>&nbsp; if (!(pSearchMatch-&gt;SERetFlags &amp; SE_FMATCH))</tt><br>
<tt>&nbsp; &nbsp; return( NOERROR );</tt><br>
<br>
<tt>&nbsp; if (Error = GetNoteClassAndDumpCount( hDB,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pSearchMatch-&gt;ID.NoteID, /* Bus Error Here !! */</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; szClass,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; LINELENGTH,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;dwDumpCount ))</tt><br>
<tt>&nbsp; {</tt><br>
<tt>&nbsp; &nbsp; return (Error);</tt><br>
<tt>&nbsp; }</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </tt><br>
<tt>/* ... etc... */<br>
</tt><br>
<br>
After porting to UNIX:<br>
<br>
<tt>/************************************************************************</tt><br>
<br>
<tt>&nbsp; FUNCTION: &nbsp;DumpOneNote</tt><br>
<br>
<tt>&nbsp; PURPOSE: &nbsp;This is the action routine specified to NSFSearch</tt><br>
<br>
<tt>&nbsp; INPUTS: &nbsp; void far *Param &nbsp; &nbsp; &nbsp; &nbsp; - not used</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; SEARCH_MATCH far *pSearchMatch - information about the</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;note that was found</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; ITEM_TABLE far *SummaryBuffer &nbsp;- not used</tt><br>
<br>
<tt>*************************************************************************/</tt><br>
<br>
<tt>STATUS LNPUBLIC DumpOneNote( void far * Param,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;SEARCH_MATCH far *pSearchMatch,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ITEM_TABLE far * SummaryBuffer )</tt><br>
<tt>{</tt><br>
<tt>&nbsp; SEARCH_MATCH	SearchMatch;</tt><br>
<tt>&nbsp; STATUS Error;</tt><br>
<tt>&nbsp; char &nbsp;szClass[LINELENGTH+1];</tt><br>
<tt>&nbsp; DWORD &nbsp;dwDumpCount;</tt><br>
<br>
<tt>&nbsp; memcpy( (char*)&amp;SearchMatch, (char*)pSearchMatch, sizeof(SEARCH_MATCH) );</tt><br>
<br>
<tt>&nbsp; if (!(SearchMatch.SERetFlags &amp; SE_FMATCH))</tt><br>
<tt>&nbsp; {</tt><br>
<tt>&nbsp; &nbsp; return( NOERROR );</tt><br>
<tt>&nbsp; }</tt><br>
<br>
<tt>&nbsp; if (Error = GetNoteClassAndDumpCount( hDB,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; SearchMatch.ID.NoteID,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; szClass,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; LINELENGTH,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;dwDumpCount ))</tt><br>
<tt>&nbsp; {</tt><br>
<tt>&nbsp; &nbsp; return (Error);</tt><br>
<tt>&nbsp; }</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </tt><br>
<tt>/* ... etc... */</tt><br>
<br>
<tt><br>
</tt><b><font size="4" color="#000080">Step 6: Remove Constructs not Supported by Your C Compiler</font></b><br>
<br>
Remove from your code (or conditionally compile) any constructs that the C compiler on your UNIX system does not support. <br>
<br>
For example, many programs developed using Microsoft C use the double forward slash ( // ) comment delimiter, a C and C++ convention that Microsoft supports for compatibility with its C++ compiler. <br>
<br>
<b><font size="4" color="#000080">Step 7: Check All Explicit File Names</font></b> <br>
<br>
All file names should be in lowercase unless there is a good reason to do otherwise. Remember that file names in UNIX are case-sensitive. The biggest impact of this change is on documentation, with a smaller impact on source code.<br>
<br>
Many programs and almost all documentation under DOS use all uppercase letters for file names. This helps to distinguish file names from other text in documentation, but under UNIX it is generally wrong because file names are in lowercase.
---
