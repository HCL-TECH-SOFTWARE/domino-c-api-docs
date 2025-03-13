##### Chapter 3-1
##### Building Windows Applications

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
The HCL C API Toolkit for Domino and Notes lets you build Windows(32 or 64 bit) applications using the Microsoft Visual C++ tools that run with the release of HCL Domino or HCL Notes for all supported Windows platforms.  This chapter describes the details specific to building C API applications in the Windows environment. It covers the following topics:<br>

<ul><b>Getting Started</b><br>
Hardware and software requirements, compiler and toolkit installation requirements, environment settings, and toolkit installation<br>
<br>
<b>Program Structure</b><br>
Initialization and file-naming conventions<br>
<br>
<b>Toolkit Files</b><br>
Platform-specific files supplied with the HCL C API Toolkit for Domino and Notes<br>
<br>
<b>Compatibility</b><br>
Information on addressing, calling conventions, and data alignment<br>
<br>
<b>Compiling, Linking, and Debugging</b><br>
Platform-specific information on compiler, linker, and debugger settings for C API applications<br>
<br>
<b>Microsoft Visual Studio 2017/2022</b><br>
Building applications using the GUI environment for Visual Studio 2017/2022</ul>
<br>
<br>
<b><font size="5" color="#000080">Getting Started</font></b><br>
<br>
<b><font size="4" color="#000080">Hardware Required</font></b><br>
<br>
Same requirements as Notes/Domino with addition of space for HCL C API Toolkit and compilation<br>
<br>
<b><font size="4" color="#000080">Software Required</font></b><br>
<br>
The following software is required to develop HCL C API programs for the Notes client:<br>

<ul type="disc">
<li>HCL Domino or HCL Notes 14.5 for Windows. All Windows platforms supported by Notes 14.5 are also supported by this toolkit.
<li>Microsoft Visual Studio 2017/2022. </ul>
<br>
The following software is required to develop HCL C API programs for Domino:<br>

<ul type="disc">
<li>HCL Domino or HCL Notes 14.5 for Windows.  All Windows platforms supported by Domino 14.5 are also supported by this toolkit. 
<li>Microsoft Visual Studio 2017/2022. </ul>
<br>
<br>
<b><font size="4" color="#000080">Compiler Installation</font></b><br>
<br>
Windows support a flat, 32-bit memory model for all programs.<br>
<br>
<br>
<b><font size="4" color="#000080">Environment Settings</font></b><br>
<br>
Set the following environment variables before building or running HCL C API programs for Domino and Notes under Windows.<br>
<br>
Environment variables may be set in a variety of ways.  For example, they may be set in the Environment Variables section of your system settings, in a batch file, in a program, or in a makefile.  For more information, refer to the Windows documentation.  You may need to restart Windows for the new configuration to take effect.<br>
<br>
References to &quot;<i>d:</i>&quot; in the descriptions below refer to the appropriate fixed disk letter.<br>
<br>
PATH should contain:<br>

<ul type="disc">
<li>The Microsoft C compiler directory which is normally located in the Visual C++ 2017/2022 bin directory.
<li>The Domino or Notes program directory; normally <i>d:</i>\lotus\notes. The Domino or Notes program directory contains the Domino or Notes executables and DLLs.  This is required if the DLLs are loaded implicitly.  As an alternative, the DLLs may be loaded explicitly by an application.  See the chapter &quot;Program Structure:  Overview&quot; in this <i>User Guide</i> for more information.</ul>
<br>
LIB should contain: <br>

<ul type="disc">
<li>The HCL C API libraries directory; normally <i>d:</i>\notesapi\lib\mswin32(or <i>d:</i>\notesapi\lib\mswin64 for 64 bit Windows).
<li>The Microsoft C libraries directory</ul>
<br>
INCLUDE should contain: 
<ul>
<ul></ul>

<li type="disc">The HCL C API include files directory: normally <i>d:</i>\notesapi\include.
<li type="disc">The Microsoft C include files directory</ul>
<br>
Common makefile environment file:<br>
 This file has the common compilation options that used to compile C-API samples code in windows. Set the PATH environment to the C-API samples folder,<br>
set PATH=d:\notesapi\<br>
<br>
<b><font color="#000080">Header File Conflict</font></b><br>
<br>
The Microsoft Visual Studio 2017/2022 and the HCL C API Toolkit for Domino and Notes contain some include files with the same name (such as mq.h, neterr.h and stats.h) but the contents of the files differ. If your API program requires the HCL C API header file for Domino and Notes but does not require the Visual C++ 2017/2022 version of the file, you may resolve the conflict by putting the HCL C API for Domino and Notes include path before the Visual C++ 2017/2022 include path in your INCLUDE environment variable. Alternatively, you may specify the full path of the header file in the #include statement in your source code. This alternative allows your program to include both files in a single source module.<br>
<br>
The header file in the HCL C API Toolkit for Domino and Notes, global.h, contains a definition for the data type QWORD that is also defined in the Microsoft Visual C++ 2017/2022 header file, sqltypes.h.   Although the definitions ultimately result in the same data type, the syntax of the definitions cause errors when compiling source code that includes both header files.  In such cases it is recommended to keep code that requires the sqltypes.h header file in a separate module.<br>
<br>
<br>
<b><font size="4" color="#000080">Testing the Installation</font></b><br>
<br>
After installing Domino or Notes, the C compiler, the development files, the documentation, and the sample API programs, follow these steps to build and test the sample API program introwin.exe.<br>

<ol type="1">
<li>Verify that Domino or Notes executes successfully in your environment. HCL C API programs for Domino and Notes require that Domino or Notes be installed properly in the environment. <br>

<li>From the Windows program manager, start an MS-DOS Command Prompt.<br>

<li>Change to the directory containing the sample program INTROWIN. Normally, this is<br>
<br>
<i>d:</i>\notesapi\samples\basic\introwin<br>

<li>Type DIR to list the files in this directory. This directory contains the Windows makefile, mswin32.mak(or mswin64.mak for 64 bit Windows).<br>

<li>Enter this at the command prompt to build introwin.exe:<br>
<br>
<tt>nmake /f mswin32.mak or mswin64.mak /a</tt>   <br>
<br>
The program should compile and link with no errors. The resulting executable, introwin.exe, is a Windows program.<br>

<li>Make sure the database, intro.nsf, is in the Domino or Notes data directory.<br>

<li>From either the File Manager or the MS-DOS Command Prompt, run the program introwin.exe. The &quot;Intro Notes API Program&quot; window should open with a File menu option.<br>

<li>Select File - Get Database Title. The &quot;Get Database Title&quot; dialog box appears. Type &quot;<tt>intro</tt>&quot; in the &quot;Get Database Name&quot; edit field. Select OK.<br>
<br>
A dialog box should display the following output:<br>
<br>
<tt>Database title: API Test Database (intro)</tt></ol>
<br>
<br>
<b><font size="5" color="#000080">Program Structure</font></b><br>
<br>
<b><font size="4" color="#000080">Initializing the Domino or Notes Run-Time System</font></b><br>
<br>
A C API program may use any of the following methods to initialize the Domino or Notes run-time system:<br>

<ul><b><font color="#000080">NotesMain</font></b><br>
<br>
You can structure a C API program as a subroutine named NotesMain. In this case, link with the bootstrap object file \notesapi\lib\mswin32\notes0.obj(change mswin32 to mswin64 for 64 bit Windows). This object file provides the &quot;main&quot; program required by Microsoft Windows.<br>
<br>
NotesMain uses the __stdcall calling convention. The argument count provided to the subroutine is a integer and the argument vector pointers are flat memory model pointers.<br>
<br>
<br>
<b><font color="#000080">AddInMain</font></b><br>
<br>
Server add-in tasks, like NotesMain programs, must also be applications. Server add-in tasks are usually structured as a subroutine named AddInMain. You must link this type of program with both bootstrap object files, \notesapi\lib\mswin32\notes0.obj and \notesapi\lib\mswin32\notesai0.obj(change mswin32 to mswin64 for 64 bit Windows). These object files provide the &quot;main&quot; program and the server add-in initialization.<br>
<br>
In the Windows environment, you can build programs as either &quot;console&quot; or &quot;gui&quot; (Graphical User Interface) applications. If you build a server add-in task as a &quot;gui&quot; application, Windows creates a new console window when the first message is written to the server console (for example, by AddInLogMessageText). To have messages from a server add-in appear in the server console window, you must link the application as a &quot;console&quot; application. The sample programs in the HCL C API Toolkit for Domino and Notes use the standard link options &quot;$(conflags)&quot; and &quot;$(conlibs)&quot; defined in the file win32.mak in the Microsoft Win32 SDK. When you build a server add-in using Visual C++ 2010/2022, you must create the project as a &quot;console&quot; application.<br>
<br>
Like NotesMain, AddInMain uses the __stdcall calling convention. The argument count provided to the subroutine is a integer and the argument vector pointers are flat memory model pointers.<br>
<br>
<br>
<b><font color="#000080">main</font></b><br>
<br>
You can structure the program as a standard C or C++ program with entry point main. In this case, the program must call the function NotesInitExtended to explicitly initialize the Domino or Notes run-time system before calling any other HCL C API functions. When the program no longer needs to call any C API functions, it must call the function NotesTerm to terminate the Domino or Notes run-time system explicitly.<br>
<br>
<br>
<b><font color="#000080">MainEntryPoint</font></b><br>
<br>
You can structure the program as an executable program library (DLL) with a main entry point named MainEntryPoint. In this case, the C API program is a configured as an add-in to the software. Typically, the Notes workstation or Domino server software loads and calls the main entry point of this custom library in response to a Notes user's command, menu selection, or server event. In this case, the Domino or Notes run-time system is initialized before MainEntryPoint receives control. The Domino or Notes run-time system is terminated when Domino or Notes is terminated.<br>

<ul></ul>
</ul>
<b><font size="4" color="#000080">Naming Conventions</font></b><br>
<br>
HCL Domino Server add-in programs and menu add-ins use a Domino-specific naming convention. The name of a Windows server or menu add-in must begin with &quot;n&quot;, followed by one to seven characters and the appropriate file extension (.exe or .dll). For example, the sample program basic\add_res, when built as a Windows application, has the name nadd_res.exe.<br>
<br>
There are no other naming restrictions for HCL C API applications for Domino and Notes. Any other type of C API application may use any valid program file name.<br>
<br>
<br>
<b><font size="5" color="#000080">Toolkit Files</font></b><br>
<br>
This section describes the components of the HCL C API Toolkit for Domino and Notes that support the Microsoft Visual C++ 2010 compiler and linker.<br>
<br>
<br>
<b><font size="4" color="#000080">HCL C API Header Files for Domino and Notes</font></b><br>
<br>
In the HCL C API Toolkit for Domino and Notes, support for all platforms is provided by the common include files in \notesapi\include. When compiling, the header files require the use of the compiler command-line switch &quot;-DWIN32&quot; to enable conditional compilation features specific to Win32.<br>
<br>
<br>
<b><font size="4" color="#000080">HCL C API Library File for Domino and Notes</font></b><br>
<br>
The file \notesapi\lib\mswin32\notes.lib(change mswin32 to mswin64 for 64 bit Windows) is the DLL import library needed to link HCL C API applications that make calls to HCL Domino or HCL Notes.  If your application loads the Notes DLLs explicitly, you do not need to link notes.lib. <br>
<br>
<b><font size="4" color="#000080">HCL C API Bootstrap Object Files for Domino and Notes</font></b><br>
<br>
The bootstrap object files in the directory \notesapi\lib\mswin32(change mswin32 to mswin64 for 64 bit Windows) are required to construct a API program using the NotesMain entry point and to construct server add-in tasks. The file notes0.obj provides the entry point and Domino or Notes run-time initialization for applications. The file notesai0.obj is used in conjunction with notes0.obj to provide the entry point and run-time initialization for HCL Domino Server add-in tasks.<br>
<br>
<b><font size="4" color="#000080">HCL C API Editfax library</font></b><br>
<br>
The file \notesapi\lib\mswin32\editfax.lib(change mswin32 to mswin64 for 64 bit Windows) is the Editfax import library needed to link HCL C API applications that implement the Editfax APIs.<br>
<br>
<br>
<b><font size="5" color="#000080">Compatibility</font></b><br>
<br>
HCL Domino and HCL Notes 14.5 support applications developed using the HCL C API Toolkit for Notes/Domino 14.5 as well as existing Domino and Notes Releases (providing that Release/Build environment is supported on the given Windows OS). <br>
<br>
<b><font size="4" color="#000080">Data Addressing and Pointers</font></b><br>
<br>
HCL C API functions for Domino and Notes expect all addresses and pointers to be pointers in the flat-model virtual memory space.<br>
<br>
<br>
<b><font size="4" color="#000080">Calling Conventions</font></b><br>
<br>
Most HCL C API functions for Domino and Notes use the __stdcall calling convention, just as the Windows API does. A few functions require a variable number of parameters; these functions use the cdecl calling convention. Under normal circumstances, specifying the appropriate calling convention is handled by the C API header files.<br>
<br>
<br>
<b><font size="4" color="#000080">Data Structure Packing</font></b><br>
<br>
Is dependent on the compiler and bitness of the program and controlled via the compiler flags<br>
<br>
<br>
<b><font size="5" color="#000080">Compiling</font></b><br>
<br>
This section describes the settings to use when building HCL C API applications for Domino and Notes from the command line or via a makefile. To build applications with the Visual C++ 2017/2022 developer environment, please refer to the &quot;Microsoft Visual C++ 2017/2022&quot; section below<i>.</i><br>
<br>
<br>
<b><font size="4" color="#000080">Platform ID Macro</font></b><br>
<br>
The HCL C API include files for Domino and Notes use the platform ID macro for conditional compilation that depends on the target execution environment. You can also use this macro in API applications to control compilation of platform-dependent features. For 32-bit Windows applications, the platform ID macro is W32. The old macro, NT, is still supported for compatibility with existing API applications.  Be aware that the UNIX platform ID macro also defines the W32 platform ID macro.  If you need conditional compilation for 32-bit Windows, but not for UNIX, be sure to check that W32 is defined and UNIX is not defined.  Alternatively you can use the NT platform ID macro for 32-bit Windows conditional compilation.<br>
<br>
<br>
<b><font size="4" color="#000080">Compiler Switches</font></b><br>
<br>
To compile HCL C API code for Windows, please follow the guidelines in the appropriate cmp.txt file (w32_cmp.txt for 32 bit, w64_cmp.txt for 64 bit)<br>
<br>
<br>
<b><font size="5" color="#000080">Linking</font></b><br>
<br>
<b><font size="4" color="#000080">Stack Size</font></b><br>
<br>
Stack space on Win32 platforms is managed dynamically, with default settings that may be modified in an application. As a general guideline, at least 2,048 bytes of stack space should be available when calling a HCL C API application for Domino or Notes.<br>
<br>
<br>
<b><font size="4" color="#000080">Linker Switches</font></b>
<ul></ul>
Please see the appropriate cmp.txt file<br>
<br>
<br>
<b><font size="4" color="#000080">Run-Time Libraries</font></b><br>
<br>
The HCL C API for Domino and Notes is implemented as a dynamic-link library (DLL) which is statically linked to the multi-threaded version of the Microsoft C run-time library.  Domino and Notes do not require installation of the Microsoft run-time DLLs.  However, the Microsoft linker reports a warning if applications are linked with both the C API library and the Microsoft DLL run-time libraries.  This is because of problems that occur when applications and DLLs are linked with different versions of the C run-time libraries.  Multiple copies of information are stored in different memory blocks, and the application and DLL must be designed to ensure that resources such as memory or files and handles allocated by one instance of the C run-time library are used and released by the that instance.<br>
<br>
The HCL C API for Domino and Notes does not share C run-time memory or file handles with the application.  Applications may be linked with any version of the Microsoft C run-time libraries.  To avoid this warning, applications must be linked with the statically-linked C run-time libraries.
<ul></ul>
For more information on the limitations on C runtime libraries, and information on how statically-linked and dynamically-linked run-time libraries can be combined, please consult the Microsoft <i>Visual C++ 2010 </i> documentation, or see Microsoft Knowledge Base article Q94248, &quot;Using the C Run-Time&quot;.<br>
<br>
For applications built using the standard macros from win32.mak, you can use the following macros:<br>

<ul>cvars	for compiling single-threaded applications or DLLs<br>
cvarsmt	for compiling multi-threaded applications or DLLs<br>
conlibs	for linking single-threaded console applications<br>
conlibsmt	for linking multi-threaded console applications<br>
guilibs	for linking single-threaded GUI applications or DLLs<br>
guilibsmt	for linking multi-threaded GUI applications or DLLs<br>
olelibs	for linking single-threaded OLE applications or DLLs<br>
olelibsmt	for linking multi-threaded OLE applications or DLLs</ul>
<br>
If you want to link with the dynamically-linked run-time libraries, you can use the following macros:<br>

<ul>cvarsdll	compile using DLL version of run-time libraries<br>
conlibsdll	link console applications using DLL version of run-time libraries<br>
guilibsdll	link GUI applications or DLLs using DLL version of run-time libraries<br>
olelibsdll	link OLE applications or DLLs using DLL version of run-time libraries<br>
<br>
</ul>
<b><font size="5" color="#000080">Microsoft Visual C++ 2017/2022 Development Environment (64 bit)</font></b><br>
<br>
This section describes Microsoft Visual C++ 2017/2022 development environment project settings that are required when you are building applications that use the HCL C API for Domino and Notes.<br>
<br>
<b><font size="4" color="#000080">Directory Settings</font></b><br>
<br>
You must specify the HCL C API  for Domino and Notes include file and library file directories in the Visual C++ 2017/2022 directory settings:<br>
<br>
I.	Select &quot;Project  - Properties ...&quot; to open the Options dialog box. 		<br>
II.	Select the &quot;VC++&quot; Directories <br>
III.	Select Include Directories and add the HCL C API include file directory (for example, c:\notesapi\include) <br>
IV.	Select Library directories and add the HCL C API library file directory (for example, c:\notesapi\lib\mswin64)<br>
<br>
These settings change the environment maintained by the Visual C++ 2017/2022 and will be retained for all projects.<br>

<p><b><font size="4" color="#000080">Project Settings</font></b><br>
<br>
Project settings specify what file to run and where to run it.<br>
<br>
I.	Select &quot;Project - Properties...&quot; to open the project's Property Pages dialog box.<br>
II.	Expand the &quot;Configuration Properties&quot; folder, then the &quot;Debugging&quot; category.<br>
III.	Enter the name of the program executable in the &quot;Command&quot; field.<br>
IV.	Enter the path to the Domino or Notes executable directory in the &quot;Working Directory&quot; field.<br>
V.	If the file notes.ini is located somewhere other than the Windows system directory or the Domino or Notes program directory, enter an &quot;=&quot; sign followed by the fully-qualified pathname of the notes.ini file in the &quot;Command Arguments&quot; field. For example, if the notes.ini file is in the directory &quot;d:\apps\notes,&quot; enter:<br>
<br>
=d:\apps\notes\notes.ini<br>
<br>
<br>
<b><font size="4" color="#000080">Compiler Settings</font></b><br>
<br>
The compiler settings correspond to the compiler switches and input options required when building applications from the command line:<br>
<br>
I.	Select &quot;Project - Properties...&quot; to open the project's Property Pages dialog box.  Expand the &quot;Configuration Properties&quot; folder. <br>
II.	 If you wish, select the &quot;General&quot; category  and set the &quot;Output Directory&quot; field to specify the relative directory for your program.<br>
III.	Select the &quot;Debugging&quot; category.<br>
IV.	Enter the path to the Domino or Notes installation directory in the &quot;Working Directory&quot; field.<br>
V.	Select the &quot;C/C++&quot; sub-folder. Note that this sub-folder is not available if the project uses a makefile that was not created by the Visual C++ 2017/2022. In this case, you must use the compiler switches described above on the compiler command line.<br>
VI.	Compiler settings are entered by choosing a category. <br>
VII.	Select  &quot;Active Debug&quot; configuration and platform x64<br>
VIII.	We recommend setting the &quot;Warning level&quot; to &quot;Level 3&quot; under the &quot;General&quot; category. This corresponds to the switch /W3.<br>
IX.	Select the &quot;Code Generation&quot; category.<br>
X.	Select an appropriate entry from the &quot;Runtime Library&quot; pull-down menu. The compatible libraries are:<br>
<br>
Multi-Threaded (/MT)<br>
Single-Threaded Debug (/MTd)<br>
Multi-Threaded DLL (/MD)                                                                                                                 Muti-Threaded DLL Debug (/MDd)
<p>XI.	Select the appropriate setting from the &quot;Struct Member Alignment:
<ul><br>
</ul>
<br>
<b><font size="4" color="#000080">Link Settings</font></b><br>
<br>
The only link settings relevant to the HCL C API for Domino and Notes are the selection of object and library modules:<br>
<br>
I.	Select &quot;Project - Properties...&quot; to open the project's Property Pages dialog box.  Expand the &quot;Configuration Properties&quot; folder. <br>
II.	Select the &quot;Linker&quot; sub-folder. Note that this tab is not available if the project uses a makefile that was not created by the Visual C++ 2017/2022. In this case, you must use the linker switches described above on the linker command line.<br>
III.	Linker settings are entered by choosing a category. Select the &quot;Input&quot; category.<br>
IV.	In the &quot;Additional Dependencies&quot; field, add notes.lib.<br>
V.	If your application is a NotesMain application, add notes0.obj.<br>
VI.	If your application is a HCL Domino Server add-in, add notesai0.obj and notes0.obj.<br>
VII.	If your application implements the Editfax APIs, add editfax.lib.<br>
If you are linking with notes0.obj and are using a run-time library other than libc.lib, select the option &quot;Ignore All Default Libraries&quot; to ignore the default library information in notes0.obj. This corresponds to the
<p>
<p><b><font size="4" color="#000080">Debugging with the Visual C++ 2017/2022</font></b><br>
<br>
There are no special considerations for debugging applications or DLLs that make calls to the HCL C API for Domino and Notes. The only special considerations are for DLLs that are called from Domino or Notes, such as menu add-ins, hook drivers, or Extension Manager DLLs. The following instructions apply only to debugging DLLs that are called from Domino or Notes.<br>
<br>
Normally, Domino and Notes expect to find any DLLs that it must load in the directory where the Domino or Notes executables are installed. To specify that DLLs built using the Visual C++ 2017/2022 are placed in this directory:<br>
<br>
I.	Select &quot;Project - Properties...&quot; to open the project's Property Pages dialog box.<br>
II.	Expand the &quot;Configuration Properties&quot; folder and select the &quot;General&quot; category.<br>
III.	Enter the path of the Domino or Notes installation directory in the &quot;Output Directories&quot; field.<br>
<br>
The Notes user interface is implemented as a loader program, notes.exe, and the workstation executable. To debug a DLL that is loaded by Notes, you must specify the workstation executable (not notes.exe) for Visual C++ 2017/2022 :<br>
<br>
I.	Select &quot;Project - Properties...&quot; to open the project's Property Pages dialog box.<br>
II.	Expand the &quot;Configuration Properties&quot; folder and select the &quot;Debugging&quot; category.<br>
III.	Enter the name of the Notes workstation executable, <b>notes.exe</b>, in the &quot;Command&quot; field.<br>
IV.	Enter the path to the Notes installation directory in the &quot;Working Directory&quot; field.<br>
If the file notes.ini is located somewhere other than the Windows system directory, enter an &quot;=&quot; sign followed by the fully-qualified pathname of the notes.ini file in the &quot;Command Arguments&quot; field. For example, if the notes.ini file is in the directory &quot;d:\apps\notes,&quot; enter:<br>
<br>
=d:\apps\notes\notes.ini
<p>
<p><br>
<b><font size="5" color="#000080">Building 32-bit Windows Applications with IBM VisualAge C++</font></b><br>
<br>
You can build C API applications with the IBM VisualAge C++ toolkit.  However, please note that the C API toolkit does not fully support the IBM VisualAge C++ toolkit  nor has it been thoroughly tested with IBM VisualAge C++.<br>
<br>
Programs built with the IBM VisualAge C++ must be &quot;main&quot; programs.  You will not be able to use NotesMain or AddinMain because these rely on notes0.obj or notesai0.obj which are not compatible with the IBM VisualAge C++ compiler and linker.<br>
<br>
Here is an example of an IBM VisualAge C++ makefile to build an application with IBM Visual Age.  This example will build the basic\intro program that comes with the C API toolkit.<br>

<ul><tt>PROGNAME = INTRO</tt><br>
<br>
<tt># Dependencies<br>
$(PROGNAME).EXE: $(PROGNAME).OBJ<br>
$(PROGNAME).OBJ: $(PROGNAME).C</tt><br>
<br>
<tt># Compilation command. <br>
.C.OBJ:<br>
 &nbsp; &nbsp;icc /C+ /Gm+ /Sp1 /DW32 /W3 $*.C</tt><br>
<br>
<tt># Link command.<br>
 <br>
.OBJ.EXE:<br>
 &nbsp; &nbsp;ILINK /OUT:$*.EXE $*.OBJ notes.lib</tt></ul>

---
