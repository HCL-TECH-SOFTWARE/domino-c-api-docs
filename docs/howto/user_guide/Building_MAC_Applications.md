##### Chapter 3-4
##### Building MAC Applications

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
This chapter identifies the hardware and software requirements for developing HCL C API programs for Notes under MAC and explains how to set up your MAC environment. It covers the following topics:<br>

<ul><b>Getting Started</b><br>
Hardware and software requirements, Compiler installation, Environment settings for compiling the sample, Running HCL C API programs, and Testing the installation<br>
<br>
<b>Program Structure</b><br>
Initialization and file-naming conventions<br>
<br>
<b>Toolkit Files</b><br>
Platform-specific files supplied with the HCL C API Toolkit for Notes<br>
<br>
<b>Compatibility</b><br>
Information on addressing, calling conventions, and data alignment<br>
<br>
<b>Compiling, Linking, Building shared libraries, and Debugging</b><br>
Platform-specific information on compiler, linker, and debugger settings for C API applications<br>
</ul>
<br>
<b><font size="5" color="#000080">Getting Started</font></b><br>
<br>
This section describes the hardware and software requirements for MAC platform supported by the HCL C API for Notes.<br>
<br>
<br>
<b><font size="4" color="#000080">Hardware and software requirements</font></b><br>
<br>
Are identical to those required by Domino with addition of space for the HCL C API Toolkit and compilation<br>
<br>
<br>
<b><font size="4" color="#000080">Compiler installation</font></b><br>
<br>
There are no special requirements for installation of the compilers or other tools. <br>
<br>
<br>
<b><font size="4" color="#000080">Environment settings for compiling the sample</font></b><br>
<br>
This section explains how to set up your MAC environment to build and run HCL C API programs for Domino. <br>
<br>
<b><font color="#000080"> Summary</font></b>
<ul>
<li type="disc">Make sure HCL Notes Client for MAC and the HCL C API for Notes are installed.
<li type="disc">Set the environment variable LOTUS to HCL C API for Notes directory.
<li type="disc">Set the environment variable PATH to include the Notes Client executable directory. 
<li type="disc">Set the environment variable DYLD_LIBRARY_PATH to include the Notes Client executable.
<li type="disc">Set the environment variable Notes_ExecDirectory to specify the the Notes Client executable directory. <br>
</ul>
<br>
The sections that follow define the following concepts:
<ul>
<li type="disc">The canonical Lotus directory 
<li type="disc">The Notes executable directory<br>
</ul>
<br>
<b><font color="#000080"> The canonical Lotus directory</font></b><br>

<ul>Set the environment variable <tt><b>LOTUS</b></tt> to point to HCL C API for Notes directory:
<ul>
<ul>
<li type="disc">The directory where you uncompress the HCL C API Toolkit, for example: /Users/notes</ul>
</ul>
<tt>&nbsp; &nbsp; </tt><br>
If you use the C shell, your .cshrc file should contain the line:<br>

<ul>setenv LOTUS /User/notes			</ul>
</ul>
<br>
    For sh or ksh,  your initialization file should contain the following:<br>

<ul>
<ul>LOTUS=/User/notes<tt>; export LOTUS</tt>			<br>
</ul>
The MAC platforms support symbolic directory links. Therefore, Lotus products may physically reside anywhere in the file system, so long as a directory link in the canonical Lotus directory points to where the product actually resides. For example, the directory /User/notes/notesapi may be a symbolic link to the directory where the HCL C API Toolkit for Notes physically resides. </ul>

<ul>The make files for HCL C API sample programs use $LOTUS to locate the directory where the HCL C API for Notes include files and object files reside. <br>
</ul>
<br>
<b><font color="#000080"> The Notes executable directory</font></b><br>

<ul>The Notes executable directory is the directory where the Notes executable program libraries reside.<br>
<br>
Under MAC,the Notes Client excutable program libraries reside /Applications/Notes.app/Contents/MacOS/ by default<br>
<br>
By convention, set the environment variable <tt><b>Notes_ExecDirectory</b></tt> to point to the Notes executable directory. If you use the C shell, your .cshrc file should contain the line:<br>

<ul><tt>setenv Notes_ExecDirectory your-Notes-executable-directory</tt></ul>
</ul>
	 <br>
        For sh or ksh,  your initialization file should contain the following:<br>

<ul>
<ul><tt>Notes_ExecDirectory=your-Notes-executable-directory; </tt><br>
<tt>export Notes_ExecDirectory</tt></ul>
<br>
<br>
</ul>
<b><font size="4" color="#000080">Running HCL C API programs</font></b><br>
<br>
This section explains how to set up your MAC environment to run HCL C API programs for Notes.<br>

<p>MAC is a Notes Client only platform. It is required that you run C API programs on MAC under the same login as the client.<br>
you do not need to be a super user to change the owner and group settings of a program that you built.
<ul></ul>
<br>
<br>
<b><font color="#000080"> The initialization algorithm</font></b><br>
At initialization time, Notes and C API programs search for the Notes Client executable directory. In order to find the Notes Clients executable directory, C API programs that are written as main programs must call NotesInitExtended.
<p>This algorithm determines the Notes Client executable directory:
<p>  1.	If the Notes_ExecDirectory environment variable is set, the value of Notes_ExecDirectory is taken to be the Notes Clients executable directory.
<p>  2.	Otherwise, use argv[0]. The value of argv[0] is the name of the program as specified on the command line. If argv[0] specifies a full or relative path name, the directory portion of that pathname is taken to be the Notes Client executable directory; otherwise the PATH environment variable is used to locate the directory containing argv[0], and that directory is taken to be the Notes Client executable directory.
<p>While developing your C API program, set the Notes_ExecDirectory environment variable to specify the Notes Client executable directory in your environment.
<p><br>
<b><font size="4" color="#000080">Testing the installation</font></b><br>
<br>
After installing the Notes Clients, the C compiler, the development files, the documentation, and the sample C API programs, follow these steps to build and test the sample C API program<i> </i><b><i>intro</i></b>. Any problem building or executing an unmodified sample program indicates a problem in the environment.<br>

<ul>
<ol type="1">
<li>Verify that the Notes Clients executes successfully in your environment. C API programs require that the Notes Clients is installed properly in the environment.<br>

<li>Open an xterm window, or use rlogin or telnet to get a shell and a command prompt.<br>

<li>Under the default installation of the HCL C API Toolkit for Notes, this sample directory is located under:<br>
<br>
$LOTUS/notesapi/samples/basic/intro<br>

<li>Change to the directory where <tt><b>intro</b></tt> was copied and type <tt><b>ls</b></tt> to list the files in this directory. <br>
 <br>
The .mak files in this directory are make files for the various operating environments. The C API kit includes multiple build support files for samples that can be built for multiple platforms.<br>

<li>Build <tt><b>intro</b></tt> using the make file appropriate to your operating environment. For example,type the following command at the command prompt: <br>
<br>
<tt>make -f macosx.mak<br>
<br>
</tt>The program should compile and link with no errors.<br>

<li>Copy the database,<tt><b>&nbsp;intro.nsf</b></tt>, from the <tt><b>notedata</b></tt> directory in the C API kit to the Notes data directory.  Under the default installation of the HCL C API Toolkit for Notes, this database is located under:<br>
<br>
$LOTUS/notesapi/notedata/intro.nsf<br>

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
<li>Start Notes,Open the database &quot;<b>intro.nsf</b>&quot;. <br>

<li>Check the database title by selecting File - Database - Properties. The title should be the same as the one printed by the<tt>&nbsp;intro</tt>  sample: &quot;API Test Database (intro).&quot;<br>
<br>
</ol>
</ul>
<br>
<br>
<b><font size="5" color="#000080">Program Structure</font></b><br>
<br>
<b><font size="4" color="#000080">Program Initialization</font></b><br>
<br>
C API programs for MAC may use any of the following methods to initialize the Notes Client run-time system.<br>

<ul><b><font color="#000080">NotesMain</font></b><br>
<br>
You can structure C API programs for MAC as a subroutine named NotesMain. In this case, link with the bootstrap object file notes0.o. This object file provides the &quot;main&quot; program required by MAC systems.<br>
<br>
NotesMain uses the system's standard calling convention. The argument count provided to the subroutine is an integer.<br>
<br>
<br>
<b><font color="#000080">main</font></b><br>
<br>
You can structure the program as a standard C or C++ program with entry point main. In this case, the program must call the function NotesInitExtended to explicitly initialize the Notes Client run time system before calling any other HCL C API for  Notes functions. When the program no longer needs to call any HCL C API functions for Notes, it must call the function NotesTerm to terminate the Notes run time system explicitly.<br>
<br>
<b><font color="#000080">MainEntryPoint</font></b><br>
<br>
You can structure the program as a shared object library with a main entry point named MainEntryPoint. In this case, the C API program is configured as an add-in to the software. Typically, the Notes client software loads and calls the main entry point of this custom library in response to a Notes user's command or menu selection. In this case, the Notes Client run-time system is initialized before MainEntryPoint receives control. The Notes Client run-time system is terminated when the user exit the Notes Client.<br>
</ul>
<br>
<b><font size="4" color="#000080">Naming Conventions</font></b><br>
<br>
<b><font color="#000080">Platform-Specific File Directories</font></b><br>

<ul>The platform-specific files supplied with the HCL C API for Notes are in the library directory. The pathname for this directory depends on the platform:
<ul><br>
MAC:	$LOTUS/notesapi/lib/macosx<br>
</ul>
</ul>
<br>
<b><font color="#000080">Custom Libraries</font></b><br>

<ul>On MAC platforms, the filenames of shared objects must start with the characters &quot;lib&quot;, Append to &quot;lib&quot; the name you want to give the file, the extensions used <b><i>.dylib</i></b>  , for example,<br>
<br>
<u>Platform</u>	<u>File extension</u>	<u>Typical Filename</u><br>
MAC	            .dylib	  	libfoo.dylib</ul>
<br>
<b><font size="5" color="#000080">Toolkit Files</font></b><br>
<br>
This section describes the components of the HCL C API for Notes that support building applications for MAC platforms.<br>
<br>
<br>
<b><font size="4" color="#000080">HCL C API for Notes Header Files</font></b><br>
<br>
In the HCL C API for Notes, support for all platforms is provided by the common include files in $LOTUS/notesapi/include. When compiling, the Notes header files require the use of the many compiler command-line switches which will be detailed below and are also in the macosx_cmp.txt file included in the include directory of the SDK.<br>
For details, see &quot;Compiling,&quot; below.<br>
<br>
Be aware that the MAC platform ID macro, &quot;-DMAC&quot; also defines the &quot;-DW32&quot; platform ID macro which stands for the Win32 APIs.<br>
Detail please see the macosx_cmp.txt in the cmp folder.<br>
<br>
<b><font color="#000080">Header File Conflict</font></b><br>
<br>
It is possible that a header file that is included with the compiler's software development kit may have the same name, but different contents, as a C API for Notes header file. If your API program requires the HCL C API header file for Notes but does not require the other file that has the same name, you may resolve the conflict including the HCL C API for Notes headers before the others during compilation. Alternatively, you may specify the full path of the header file in the #include statement in your source code. This alternative allows your program to include both files in a single source module.<br>
<br>
It is also possible that a header file that is included with the compiler's software development kit may contain a definition that is also defined in a header file in the HCL C API for Notes and the syntax of the definitions cause errors when compiling source code that includes both header files.  In such cases it is recommended to keep code that requires each header file in a separate module.<br>
<br>
<br>
<b><font size="4" color="#000080">HCL C API Library Files for Notes</font></b><br>
<br>
Since the HCL C API for Notes is supplied as a shared object library on MAC platforms, no separate library files are supplied with the HCL C API Notes. For details, see &quot;Linking,&quot; below.<br>
<br>
<br>
<br>
<b><font size="5" color="#000080">Compatibility</font></b><br>
<br>
<b><font size="4" color="#000080">Data Structure Packing</font></b><br>
<br>
On MAC systems, most data structures passed between Notes and API applications are aligned on the appropriate data boundaries. However, some structures containing data that is stored directly in a Notes database are stored in Notes canonical format. You must convert this data using ODSReadMemory and ODSWriteMemory. <br>
<br>
<br>
<b><font size="5" color="#000080">Compiling</font></b><br>
<br>
<b><font size="4" color="#000080">Platform ID Macro</font></b><br>
<br>
Mac platform has a platform-specific ID macro: MAC
<ul>
<ul></ul>
</ul>
<br>
<b><font size="4" color="#000080">Compiler Switches and Options</font></b><br>
<br>
To compile Domino C API applicaitons under Linux use the switches in macosx_cmp.txt<br>
<br>
<br>
<b><font size="5" color="#000080">Linking</font></b><br>
<br>
<b><font size="4" color="#000080">Stack Size</font></b><br>
There are no special considerations for stack size for MAC C API applications for Notes.<br>
<br>
<br>
<b><font size="5" color="#000080">Building shared libraries</font></b><br>
<br>
<b><font size="4" color="#000080">Linker Switches</font></b><br>
<br>
The recommended linker switches depend on the linker you use.<br>
<br>
<b><u><font color="#000080">MAC</font></u></b><br>
To link C API applications under Linux, use the switches in macosx_cmp.txt.<br>
<br>
<b><font size="5" color="#000080">Debugging</font></b><br>
<br>
To build a version of an application for symbolic debugging, add the following flag to the compiler command:<br>
<br>
    -g	Cause the compiler to generate additional information needed by the symbolic debugger.<br>
<br>
You may want to avoid use of the -O flag, used to generate optimized code.
<ul><br>
</ul>

---
