##### Chapter 3-3
##### Building IBM i Applications

<br>
<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
The HCL C API Toolkit for Notes/Domino lets you also build IBM i applications.  However, development of IBM i applications specifically requires the HCL C API Toolkit for Notes/Domino for IBM i.  This chapter describes the details specific to building HCL C API applications for Domino in the IBM i environment.  It covers the following topics:<br>

<ul><b>Getting Started</b></ul>
       Toolkit installation, compiler requirements<br>
<br>
<b>      Toolkit Files</b><br>
<b>      </b>Accessing the IBM i toolkit header files<br>
<br>
<b>      Compiling and Linking</b><br>
<b>    </b>  Compiling and linking on the IBM i<br>
    <br>
<b>      Running the C API program</b><br>
<b>      </b>Running C API programs on the IBM i<br>
<br>
<b>      General Considerations for Using C API</b><br>
       Considerations using the  C API on the IBM i<br>
<br>
<b>      Building C applications Using CL Programs</b><br>
       Building C applications using CL programs on the IBM i<br>
<br>
<b>      Building C applications Using WebSphere Development Studio for IBM i CODE</b><br>
       Building C applications using WebSphere development studio CODE on the IBM i<br>
<br>
<b><font size="5" color="#000080">Getting Started</font></b><br>
<br>
If you did not install the HCL C API for Notes/Domino software for IBM i when you installed the Domino for IBM i software, you will need to go back and install it for now as it is not part of the HCL C API toolkit at this time.<br>
<br>
<br>
<br>
<b><font size="4" color="#000080">Compiler Requirements for C</font></b><br>
<br>
Compiling C application programs requires using the native IBM i C compiler -- ILE C compiler.    <br>
<br>
The process for creating IBM i ILE C programs or service programs includes two steps:
<ol type="1">
<li>Run the CRTCMOD (Create C Module) command to compile C source code into modules.
<li>Run the CRTPGM(Create Programs) or CRTSRVPGM(Create Service Programs) to bind modules into an ILE program or service program.</ol>
<br>
The required software to compile C programs are:
<ul type="disc">
<li>The ILE C Compiler, available as Product 5770WDS(on V7R2) Option 51.  
<li>The QSYSINC, available through the &quot;Install Licensed Program&quot; Option 13.</ul>
<br>
In addition, the CODE (CoOperative Development Environment) component of the WebSphere Development Studio Client for IBM i provides tools to develop, compile and link the C programs.  For further information on obtaining the  WebSphere Development Studio Client for IBM i go to:<br>
	<a href="http://www.ibm.com/software/ad/wdt400">http://www.ibm.com/software/ad/wdt400</a><br>
<br>
<br>
<b><font size="5" color="#000080">Toolkit Files</font></b><br>
<br>
When you install the C API support software on IBM i, the C header files are installed in the library QNOTESAPI. Within this library, the header files are members of the IBM i file H.FILE (QNOTESAPI/H).  The installation also creates symbolic links /qibm/proddata/lotus/notesapi/include/*.h to the header file members. <br>
<br>
The source code of a C application can be stored as a &quot;Root&quot; file system file in IFS (Integrated File System), or as a member of a physical file.  It is recommended to keep the source in an IFS file.<br>
<br>
If you compile the C application programs with the source code in the Integrated File System, the compiler will access the headers through the symbolic links.  You only need to specify the symlnk directory /qibm/proddata/lotus/notesapi/include with the compiler Include Directory parameter (INCDIR).<br>
 <br>
If you compile the C application programs with the source code as a member of a physical file, the ILE C compiler can access the headers as they are installed in the QNOTESAPI library.  You only need to add the QNOTESAPI to your library list.<br>
<br>
<br>
<b><font size="5" color="#000080">Compiling and Linking</font></b><br>
<br>
The IBM i ILE C/C++ Programmer's Guide (SC09-2712) describes how to compile a C program using the ILE C compiler. In using the procedures described in that book, you need to follow either the IFS or physical file instructions below to compile the C application and then do the linking.<br>
<br>
<b><font size="4">Compiling the C application with the source as an IFS file</font></b><br>
<br>
Compile the application using CRTCMOD command.  You need to specify the path name of the source file in SRCSTMF compiler parameter.  Also, specify the Include Directory in the parameter INCDIR and define names of OS400 and UNIX in DEFINE parameter.  For example:<br>
<tt><b>	CRTCMOD MODULE(ctest/foo) </b></tt><br>
<tt><b>		SRCSTMF('ctest/foo/foo.c') </b></tt><br>
<tt><b>		DEFINE(OS400 UNIX) SYSIFCOPT(*IFSIO) </b></tt><br>
<tt><b>		INCDIR('/qibm/proddata/lotus/notesapi/include')</b></tt><br>
<br>
This command creates a module called FOO.MODULE in the library CTEST on the IBM i.<br>
<br>
<b><font size="4">Compiling the C application with the source as a member of physical file</font></b><br>

<ol type="1">
<li>Put the QNOTESAPI library in your library list. For example, enter this IBM i command: <br>
<tt><b>ADDLIBLE QNOTESAPI</b></tt><b><br>
</b>
<li>Specify a define name of OS400 when you compile the C module on IBM i (CRTCMOD command). For example: </ol>
<tt><b>&nbsp; &nbsp;crtcmod module(ctest/foo) define(os400)<br>
<br>
</b></tt>This command creates a module called FOO.MODULE in the library CTEST on the IBM i.<br>
<br>
<br>
<b><font size="4" color="#000080">Linking the C application</font></b><br>
<br>
After compiling the C module with the source in either an IFS file or a physical file , link the module into a program (CRTPGM command) or a service program (CRTSRVPGM command) on the IBM i on which you compiled the module. When you use either the CRTPGM or the CRTSRVPGM command, bind in the LIBNOTES service program found in the QNOTES library. Here is a link statement that uses CRTPGM to make a program from the above compilation:<br>
<tt><b>CRTPGM PGM(CTEST/FOO) &nbsp;MODULE (CTEST/FOO) &nbsp;BNDSRVPGM (QNOTES/LIBNOTES)</b></tt><br>
<br>
The CRTPGM command creates FOO.PGM in the library CTEST.LIB.<br>
<br>
Note: It is very important to make sure that the program is bound to the LIBNOTES service program in library QNOTES.  Some applications have been found to incorrectly specify a library of *LIBL when binding to the LIBNOTES service program.  This can result in incorrect operation in a multi-versioned Domino environment.  Applications must specify library QNOTES when binding to the LIBNOTES service program in order to function correctly in a multi-versioned environment.<br>
<br>
Depending on what type of Domino application is being written, you may need to link in either or both of the NOTES0 and NOTESAI0 modules. These two modules are in the QNOTESAPI library. To link in either or both of these modules, add the module or modules to the module list of the CRTPGM or CRTSRVPGM command. For example:<br>
<tt><b>CRTPGM PGM (CTEST/FOO) MODULE(CTEST/FOO QNOTESAPI/NOTES0) </b></tt><br>
<tt><b>BNDSRVPGM (QNOTES/LIBNOTES)</b></tt><br>
<tt>or</tt><br>
<tt><b>CRTPGM PGM(CTEST/FOO) MODULE(CTEST/FOO QNOTESAPI/NOTESAI0) </b></tt><br>
<tt><b>ENTMOD(QNOTESAPI/NOTES0) BNDSRVPGM(QNOTES/LIBNOTES)</b></tt><br>
<br>
Linking in either or both NOTES0 or NOTESAI0 modules depends on the main entry pointer you used in your program. For more details, see Chapter 4 of Program Structure.  <br>
<br>
<tt>If using main() as the main entry point </tt>in your program, you may need to link with proper module in library QADRT for ASCII I/O. More details can be found at:<br>
<a href="http://www.ibm.com/partnerworld/wps/servlet/ContentHandler/pw_com_asciirt_tips">http://www.ibm.com/partnerworld/wps/servlet/ContentHandler/pw_com_asciirt_tips</a>
<ul></ul>
If the application is to run under the Domino server, you must manually create a symbolic link from the Domino server UserData directory to the location of the executable:<br>
<tt><b>ADDLNK OBJ ('/QSYS.LIB/CTEST.LIB/FOO.PGM') </b></tt><br>
<tt><b>NEWLNK('/Qibm/UserData/Lotus/Notes/foo.pgm') &nbsp;LNKTYPE (*SYMBOLIC)</b></tt><br>
<br>
<b><font color="#000080">For More Information</font></b>
<ul><br>
TBD
<ul><br>
</ul>
</ul>
<b><font size="5" color="#000080">Using the C API toolkit makefiles (CL programs) to build C applications</font></b><br>
<br>
The HCL C API toolkit provides samples to illustrate how to use the C++ APIs.  We have ported some of the samples from the HCL C API toolkit to IBM i.  For each of the IBM i samples, the toolkit provides 2 makefiles.  One is used to build the sample with the source in IFS; one is used for the sample source as a member of a physical file.  Each  makefile is an IBM i Command Line Program (CLP) and is kept as a physical file member.<br>
<br>
This is probably the easiest way to build a sample.  To build a sample, the users only need to compile the makefile (CLP source) and call the CL program.  The section &quot;Building C applications Using CL Programs&quot; contains more detail information. <br>
  <br>
<b><font size="5" color="#000080">Using the WebSphere Development Studio for iSeries CODE to build C applications</font></b><br>
<br>
CODE is a suite of tools for creating source and DDS files, and managing your project.  The CODE consists of CODE Designer, CODE Editor and CODE Program Generator. With CODE Program Generator you can specify compiler and link options, and submit requests to compile, bind or build on the host or local workstation.  As an alternative, we can use the CODE Program Generator feature to compile, link and build C applications.  The section &quot;Building C applications Using WebSphere Development Studio for iSeries CODE&quot; contains more detailed information. <br>
<br>
<br>
<b><font size="5" color="#000080">Running the C API Program</font></b><br>
<br>
Run the C API program by using the IBM i CALL command. For example, <br>
<br>
<tt><b>CALL CTEST/FOO</b></tt><br>
<br>
runs the program FOO in the CTEST library.<br>
<br>
However, to make sure that the program can access the needed resources, you must: <br>

<ul type="disc">
<li>Set a PATH environment variable that identifies the IBM i path for the resources that are needed by the program.
<li>Run the program under the QNOTES user profile so that the program has the authorities to access the resources.</ul>
<br>
<b><font size="4" color="#000080">Setting the PATH environment variable</font></b><br>
<br>
The PATH environment variable identifies:  <br>

<ul type="disc">
<li>The Domino user executable directory<br>
The path for this directory is /QIBM/UserData/Lotus/Notes.
<li>The Domino  executable directory<br>
The path for this directory is /QIBM/ProdData/Lotus/Notes.
<li>The data directory for the Domino server<br>
You specify the path for the data directory when you set up the Domino server.</ul>
<br>
With releases 6.0.3, 6.5.0 and later, Domino for IBM i supports multiple releases of Domino on the same LPAR (Logical Operating System partition), In order to support multiple releases each Domino release has its own product executable (ProdData) directory. For example, the ProdData directory for Domino 6.5.5 is /QIBM/ProdData/LOTUS/DOMINO655, the ProdData directory for Domino 9.0.1 is /QIBM/ProdData/LOTUS/DOMINO901. With multi-version capable releases, the /QIBM/ProdData/LOTUS/NOTES directory still exists, but is now a symbolic link to the primary release of Domino installed on the system.<br>
Applications using /QIBM/ProdData/LOTUS/NOTES in their PATH will continue to work, but only when one release of Domino is installed. If the system has multiple releases of Domino installed, the environment for these applications must have the correct Domino product executable directory in their PATH based on the Domino server against which they are running.  When setting the PATH environment variable, applications that use /QIBM/ProdData/LOTUS/NOTES will fail when the application tries to reference a Domino database that is on any Domino server that is not configured to use the primary release. Applications that reference /QIBM/ProdData/LOTUS/NOTES should be corrected so that the correct information is set in the PATH environment variable regardless of the Domino server's configured release. <br>
Instead of hard coding the /QIBM/ProdData/LOTUS/NOTES directory when setting the PATH environment variable in applications, it is recommended that you set the Domino server environment from within a C/C++ application using this method: 
<ul type="disc">
<li>Use the QnninSetDominoEnv API to set the Domino server environment in your application. The QnninSetDominoEnv API is passed a parameter that has the Domino server's name. The API detects the Domino server's configured release and automatically sets the PATH environment variable correctly for that Domino server's configuration, regardless of the release for which the server is configured to use. <br>
See Setting the Domino server environment when using Notes APIs for more details about these using these techniques. </ul>
   There are also two other methods to be aware of:
<ul type="disc">
<li>Use the Run Domino Command (RUNDOMCMD) CL command to launch your stand-alone application against a particular Domino server. You can submit this command to run in batch and it runs with the correct Domino server environment, under the correct user profile of QNOTES, etc. The Domino server does not need to be running for this command to work. The RUNDOMCMD command detects the Domino server's configured release and automatically sets the PATH environment variable correctly for that server's configuration regardless of the release that the Domino server is configured to use.
<li>Use the Set Domino Environment (SETDOMENV) CL command to set the Domino server environment before you run the application. The SETDOMENV command detects the Domino servers configured release and automatically sets the PATH environment variable correctly. This command should not be used in an interactive job since it sets the job user profile to QNOTES.</ul>
If you set the Domino server environment from a CL program or interactively before you run an application, you would most likely use a CL command. It is important that you do not hard code the /QIBM/ProdData/LOTUS/NOTES directory and assume that it is correct for all Domino servers. You must now consider this directory as something that can be different for each Domino server, just like the data directory for each Domino server is different.<br>
<br>
<br>
<b><font size="4" color="#000080">Running under the QNOTES user profile</font></b><br>
<br>
All programs must run under jobs that use the QNOTES user profile. The following processes run under the QNOTES profile when they are started:<br>

<ul>
<li type="disc">The Domino server
<li type="disc">Programs that are started by the Domino server as a result of ServerTasks or ServerTasksAt settings in the NOTES.INI file
<li type="disc">Programs that are started as a result of Program documents in the Domino Directory
<li type="disc">Hook drivers and extension manager applications that run in the Domino server
<li type="disc">Programs that are started as a result of entering the Load command on the Domino server console</ul>
<br>
If your application is not designed to run in the above processes (such as an interactive application), you must take some action to make sure you run under the QNOTES profile. Use one of the following ways to make your application run under the QNOTES profile:<br>
<br>
<b>Method 1:  Inside your application, swap to the QNOTES profile by using the following system APIs:</b>
<ul type="disc">
<li><tt>QSYGETPH</tt> - get profile handle
<li><tt>QWTSETP</tt> - set profile<br>
</ul>
Following is a coding example for using the IBM i APIs to swap to the QNOTES user profile:<br>
<br>
<tt>/* header files to include */</tt><br>
<tt>#include &lt;qsygetph.cleinc&gt; &nbsp; /* Header file for the QSYGETPH */</tt><br>
<tt>#include &lt;qwtsetp.cleinc&gt; &nbsp; &nbsp;/* Header file for the QWTSETP */</tt><br>
<tt>#include &lt;qusec.h&gt; &nbsp; &nbsp; &nbsp; /* Error code structure */</tt><br>
<tt>#include &lt;qsnapi.h&gt; &nbsp; &nbsp; &nbsp;/* Error code structure */</tt><br>
<br>
<tt>/* declarations */</tt><br>
<tt>Qus_EC_t err_code;</tt><br>
<tt>char &nbsp; &nbsp; &nbsp;cur_user[11] = &quot;*CURRENT &nbsp;&quot;;</tt><br>
<tt>char &nbsp; &nbsp; &nbsp;qnotes_user[11] = &quot;QNOTES &nbsp; &nbsp;&quot;;</tt><br>
<tt>char &nbsp; &nbsp; &nbsp;qnotes_password[11] = &quot;*NOPWD &nbsp; &nbsp;&quot;;</tt><br>
<tt>char &nbsp; &nbsp; &nbsp;user_prof_handle[13];</tt><br>
<tt>char &nbsp; &nbsp; &nbsp;qnotes_prof_handle[13];</tt><br>
<br>
<tt>&nbsp;/* get the handle to the QNOTES profile */</tt><br>
<tt>&nbsp;QSYGETPH(qnotes_user, qnotes_password, qnotes_prof_handle, &nbsp;&amp;err_code);</tt><br>
<tt>&nbsp;if (err_code.Bytes_Available)</tt><br>
<tt>&nbsp;{</tt><br>
<tt>&nbsp; &nbsp; &nbsp;/* Error retrieving handle to QNOTES user profile. */</tt><br>
<tt>&nbsp; &nbsp; &nbsp;return -1;</tt><br>
<tt>&nbsp;}</tt><br>
<tt>&nbsp;/* get the handle to the profile we are currently running under */</tt><br>
<tt>&nbsp;QSYGETPH(cur_user, NULL, user_prof_handle, &amp;err_code);</tt><br>
<tt>&nbsp;if(err_code.Bytes_Available)</tt><br>
<tt>&nbsp;{</tt><br>
<tt>&nbsp; &nbsp; &nbsp;/* Error retrieving handle to current user profile. */</tt><br>
<tt>&nbsp; &nbsp; &nbsp;return -1;</tt><br>
<tt>&nbsp;}</tt><br>
<tt>&nbsp;/* switch to QNOTES user profile */</tt><br>
<tt>&nbsp;QWTSETP(qnotes_prof_handle,&amp;err_code);</tt><br>
<tt>&nbsp;if(err_code.Bytes_Available)</tt><br>
<tt>&nbsp;{</tt><br>
<tt>&nbsp; &nbsp; &nbsp;/* Error switching to QNOTES user profile. */</tt><br>
<tt>&nbsp; &nbsp; &nbsp;return -1;</tt><br>
<tt>&nbsp;}</tt><br>
<br>
<tt>&nbsp;/*******************************/</tt><br>
<tt>&nbsp; &nbsp;/* &nbsp;do C APIs or functions */</tt><br>
<tt>&nbsp;/*******************************/</tt><br>
<br>
<tt>&nbsp;/* switch back to current user */</tt><br>
<tt>&nbsp;QWTSETP(user_prof_handle,&amp;err_code);</tt><br>
<tt>&nbsp;if(err_code.Bytes_Available)</tt><br>
<tt>&nbsp;{</tt><br>
<tt>&nbsp; &nbsp; &nbsp;/* Error switching to current user profile. */</tt><br>
<tt>&nbsp; &nbsp; &nbsp;return -1;</tt><br>
<tt>&nbsp;} &nbsp;</tt><br>
<br>
<br>
<b>Method 2:  Use the Submit Job command (SBMJOB) to submit the job to run under QNOTES. </b><br>
The SBMJOB command has a parameter to specify the user profile that the job should run under. Following is an example for using the SBMJOB command to run the FOO  program in the CTEST library:<br>
<tt><b>sbmjob cmd(call pgm(ctest/foo)) user(qnotes) cpyenvvar(*yes)</b></tt><br>
<br>
In addition to specifying the QNOTES user profile, this command copies the environment variable to the submitted job.<br>
<br>
To submit a job that runs under QNOTES, the user must have *USE authority to the QNOTES user profile. In general, you should avoid giving users authority to the QNOTES user profile because the QNOTES user profile has the authority to change or delete any object on your Domino server.<br>
<br>
<b>Method 3:  Use the rundomcmd utility.  </b><br>
This utility is provided as an IBM i Command Language (CL) command called RUNDOMCMD.  The RUNDOMCMD runs a given program against a server using the QNOTES user profile. <br>
<br>
RUNDOMCMD is available with the Domino version for IBM i product.<br>
<br>
The format of command is:  ( text in between &lt;&gt; is a variable that the user must supply )<br>
RUNDOMCMD SERVER(&lt;server name&gt;) CMD(CALL PGM(&lt;library&gt;/&lt;program name&gt;) PARM(&lt;optional parameters&gt;)) BATCH(*no)<br>
<br>
For example, the following will run the C API program acls in library notesapi on the server called DOM400: <br>
rundomcmd server(DOM400) cmd(call pgm(notesapi/acls) parm(acllog.nsf)) batch(*no)<br>
<br>
<b><font size="5" color="#000080">Starting server add-ins</font></b><br>
<br>
Server add-ins can be automatically started when the server starts or manually started on the server console. <br>
<br>
First, you need to create a symbolic link for the add-in in the /QIBM/UserData/Lotus/Notes directory.  For example, for a program named MyAddin that is in the library MyLibrary specify the following Add Link (ADDLNK) command to create a symbolic link:<br>
<br>
<tt><b>ADDLNK OBJ('/QSYS.LIB/MYLIBRARY.LIB/MYADDIN.PGM')</b></tt><br>
<tt><b>NEWLNK('/QIBM/UserData/Lotus/Notes/MYADDIN.PGM') LNKTYPE(*SYMBOLIC)</b></tt><br>
<br>
Once created, the symbolic link will persist even if the program is deleted and created again.<br>
<br>
Addin can now be started by:<br>
<br>
1) add the name of the add-in to the Server Task list in the notes.ini file.   When the server restarts, the add-in task will start to run.<br>
or<br>
 2) on the server console, type: load myaddin.  The add-in task will start to run. <br>
<br>
<br>
<b><font size="5" color="#000080">General Considerations for Using C API </font></b><br>
<br>
There are several requirements and restrictions for using HCL C API for IBM i:<br>
<br>
<b><font size="5" color="#000080">Restriction on APIs in exception or cancel handlers</font></b><br>
<br>
Do not put Domino APIs in exception or cancel handlers. The Domino APIs use locks to synchronize access to resources with the server. The result of putting Domino APIs in exception or cancel handlers could range from deadlocking the Domino server to requiring an ipl (restart) of your IBM i. <br>
<br>
If a Domino API is invoked in your exception or cancel handler, a deadlock could occur. If a Domino API in your application is holding a lock when an exception or cancel occurs and the handler issues another Domino API, a deadlock occurs. The effect of the deadlock depends on whether it occurs in an exception handler or a cancel handler:<br>

<ul>
<li type="disc">If the deadlock occurs in an exception handler, you need to end that job and end and restart the Domino server and any Domino applications that are running on the server. 
<li type="disc">If the deadlock occurs in a cancel handler, you need to end that job abnormally. The ENDJOBABN command must be used to end a job abnormally.</ul>
<br>
<br>
<b><font size="5" color="#000080">Using API handles</font></b><br>
<br>
API handles are 32 bits on IBM i.  If your code depends on handles being 16 bits, change your code to accommodate the 32-bit handles.<br>
<br>
<b><font size="5" color="#000080">About ASCII-to-EBCDIC conversion</font></b><br>
<br>
Domino runs internally in LMBCS (Lotus Multi-Byte Character Set), and the character string representation for the C API parameters is assumed to be LMBCS. When you write C programs using EBCDIC character strings, you must use the OSTranslate API to convert between the EBCDIC strings used by the program and the LMBCS parameters passed to and from the C APIs.
<p>You may see the samples in the C API toolkits for IBM i, where &quot;#pragma convert(850)&quot; is specified and no OSTranslate is done.  These C API programs usually work because the code page 850 (PC ASCII) is a subset of LMBCS.  Therefore, C API programs that use code page 850, or its 7-bit ASCII subset, do not need to call OSTranslate.<br>
<br>
It is recommended that you specify the &quot;#pragma convert(850)&quot; in each source file of your application.  This will free you from having to do the error-prone EBCDIC/LMBCS conversion. <br>
<br>
<b><font size="5" color="#000080">ASCII C/C++ Run Time for ASCII-EBCDIC conversion</font></b><br>
<br>
The &quot;ASCII C/C++ Run Time for IBM i&quot; provides a facility that assists in converting between ASCII and EBCDIC in applications that run on IBM i platforms.  The &quot;ASCII C/C++ Run Time&quot; allows for ASCII applications to send EBCDIC output to the IBM i and receive EBCDIC input from the IBM i.  It also enables ASCII applications to interface with many system API's, such as printf() and scanf().  You need to use such an interface layer in cases where user-written code is compiled into ASCII, such as when using the HCL C API for Notes/Domino.  By using &quot;ASCII C/C++ Run Time for IBM i&quot;, you can significantly reduce the number of changes required when porting Domino applications to the IBM i.<br>
<br>
&quot;ASCII C/C++ Run Time for IBM i&quot; includes support for only the most commonly used APIs.  For APIs that are not supported, you can use some of the inconv() routines that are built into &quot;ASCII C/C++ Run Time for IBM i&quot;. <br>
<br>
The &quot;ASCII C/C++ Run Time for IBM i&quot; is available for download at<br>
	<a href="http://www.ibm.com/partnerworld/wps/servlet/ContentHandler/pw_com_asciirt_tips">http://www.ibm.com/partnerworld/wps/servlet/ContentHandler/pw_com_asciirt_tips</a><br>
<br>
The installation of the ASCII C/C++ Run Time creates the library QADRT, which contains QADRTTS.SRVPGM, QADRTNTA.SRVPGM, QADRTMAIN.MODULE, H.FILE etc.  The installation also creates the following directory in IFS, which contains symlnks to the headers in the file QADRT/H: 	<b>/qibm/proddata/qadrt/include   </b><br>
<br>
No change to the source code is required to use the ASCII C/C++ Run Time.  The only modifications necessary are to the build process.  The preprocessor must pick up the ASCII C/C++ Run Time include file before the standard include files, and the program must bind with either of the two service programs: QADRTTS for teraspace enabled program and QADRTNTS for non-teraspace program.  Here is the modified build process.<br>

<ul type="disc">
<li>When compiling C applications (CRTCMOD), ensure that the ASCII C/C++ Run Time includes are first in the search path:</ul>
	1. If the source code is an IFS file, specify INCDIR(<b>/qibm/proddata/qadrt/include</b>, ......)<br>
	2. If the C source code is a member of a physical file, place the library QADRT at the top of the library list: ADDLIBLE QADRT.
<ul type="disc">
<li>When link C modules (CRTPGM or CRTSRVPGM), bind in the QADRTTS or QADRTNTA service program in QADST library:</ul>
	BNDSRVPGM(QADRT/QADRTTS) or BNDSRVPGM(QADRT/QADRTNTS)<br>
         Where QADRTTS supports teraspace enabled programs and QADRTNTS supports non-teraspace programs.	<font face="MS Sans Serif">	</font><br>
		
<ul></ul>
<br>
<b><font size="5" color="#000080">Additional considerations</font></b><br>
<br>
The following must also be considered when writing C API programs:
<ul type="disc">
<li>Be aware of the IBM i operating system (OS/400) restrictions for thread safety.
<li>Avoid using global new() and delete() operators.</ul>
<br>
<b><font size="4" color="#000080">Restrictions for thread safety</font></b><br>
The following programs run in processes (jobs) that can have multiple threads:
<ul type="disc">
<li>Programs that are started as a result of Program documents in the Domino Directory and any programs they call.
<li>Programs that are started as a result of entering the Load command on the Domino server console and any programs they call.</ul>
<br>
The following programs run in secondary threads:
<ul type="disc">
<li>Hook drivers and extension manager applications that run in the Domino server.
<li>C API programs that are called by the LotusScript Declare statements in agents and any programs that are called from those C programs.
<li>Programs that are specified in the LotusScript Shell statement in agents and any programs that are called by those programs.</ul>
<br>
The IBM i has restrictions on jobs capable of running multiple threads and on the use of secondary threads.  For details, see the IBM i books, <i>System API Programming</i> (SC41-5800) and <i>System API Reference</i> (SC41-5801).<br>
<br>
<b><font size="4" color="#000080">Restrictions on using global operators</font></b><br>
For service programs that are written in C++, do not use global new or delete operators in any add-in.  If you need to override those operators, confine them to class scope.  Using global new or delete operators may result in some parts of the Domino server not working correctly.  This restriction is related to an IBM i restriction that there can be only one global new and delete operator per activation group.<br>
<br>
<br>
<b><font size="5" color="#000080">Building C applications Using CL Programs</font></b><br>
<br>
We will use the C API toolkit sample &quot;acls&quot; to describe how to use the toolkit makefile (CL program) to build a C application.  Here, the ASCII C/C++ Run Time has been installed and the C program will be built with teraspace enabled.<br>

<ul type="disc">
<li> <b>Build the C API sample application &quot;acls&quot; with the source code as an IFS file /qntcsdk/samples/admin/acls/acls.c.</b></ul>
<br>
1. Create source physical file QNTCSDK/ACLS:<br>
	CRTLIB QNTCSDK<br>
	CRTSRCPF FILE(QNTCSDK/ACLS)<br>
<br>
2. Create the makefile (CL program) mk_acls_i as a member of physical file QNTCSDK/ACLS:<br>
	STRSEU SRCFILE(QNTCSDK/ACLS) SRCMBR(MK_ACLS_I) TYPE(CLP)<br>
	Type in the following CL program and save it:<br>
<br>
	PGM<br>
	     MONMSG MSGID(CPF2103)<br>
<br>
	     CRTCMOD MODULE(QNTCSDK/ACLS) +<br>
	 	    	SRCSTMF('/QNTCSDK/SAMPLES/ADMIN/ACLS/ACLS.C') +<br>
          	    	SYSIFCOPT(*IFSIO) +<br>
          		DBGVIEW(*ALL) +<br>
          		DEFINE(OS400 UNIX) +<br>
          		TGTCCSID(37) +<br>
			TERASPACE(*YES) +<br>
			STGMDL(*INHERIT) +<br>
          		INCDIR('/QIBM/PRODDATA/QADRT/INCLUDE' '/QIBM/PRODDATA/LOTUS/NOTESAPI/INCLUDE')<br>
<br>
	     CRTPGM PGM(QNTCSDK/ACLS) +<br>
          		MODULE(*PGM) +<br>
          		ENTMOD(QADRT/QADRTMAIN2) +<br>
          		BNDSRVPGM(QNOTES/LIBNOTES QADRT/QADRTNTS) +<br>
          		OPTION(*DUPVAR *DUPPROC) +<br>
          		DETAIL(*BASIC)<br>
	ENDPGM<br>
<br>
3. Compile the CL program:<br>
<br>
	1) WRKMBRPDM FILE(QNTCSDK/ACLS) select the CLP &quot;MK_ACLS_I&quot; and apply option 14=Compile.<br>
  or<br>
	2) CRTCLPGM PGM(QNTCSDK/MK_ACLS_I) SRCFILE(QNTCSDK/ACLS) <br>
<br>
4. Compile and link the C API sample &quot;acls&quot;:<br>
	CALL QNTCSDK/MK_ACLS_I<br>
    As a result, the command creates a C program acls (*PGM) in the library QNTCSDK.<br>
 <br>

<ul type="disc">
<li> <b>Build the C API sample application &quot;acls&quot; with the source code as a member of physical file qntcsdk/acls(*FILE)</b></ul>
<br>
1. Create the makefile (CL program) mk_acls_p as a member of physical file QNTCSDK/ACLS:<br>
	STRSEU SRCFILE(QNTCSDK/ACLS) SRCMBR(MK_ACLS_P) TYPE(CLP)<br>
	Type in the following CL program and save it:<br>
<br>
	PGM<br>
     		MONMSG MSGID(CPF2103)<br>
<br>
	      ADDLIBLE QNOTESAPI<br>
     		ADDLIBLE QNTCSDK<br>
     		CHGSYSLIBL QADRT<br>
<br>
	      CRTCMOD MODULE(QNTCSDK/ACLS) +<br>
     	    		SRCFILE(QNTCSDK/ACLS) +<br>
          		SYSIFCOPT(*IFSIO) +<br>
          		DBGVIEW(*ALL) +<br>
          		DEFINE(OS400 UNIX) +<br>
          		TERASPACE(*YES) +<br>
          		STGMDL(*INHERIT)<br>
<br>
     		CRTPGM PGM(QNTCSDK/ACLS) +<br>
          		MODULE(*PGM) +<br>
         		ENTMOD(QADRT/QADRTMAIN2) +<br>
          		BNDSRVPGM(QNOTES/LIBNOTES QADRT/QADRTNTS) +<br>
          		OPTION(*DUPVAR *DUPPROC) +<br>
          		DETAIL(*BASIC)<br>
<br>
	ENDPGM<br>
<br>
2. Compile the CL program:<br>
	1) WRKMBRPDM FILE(QNTCSDK/ACLS) select the CLP &quot;MK_ACLS_P&quot; and apply option 14=Compile.<br>
  or<br>
	2) CRTCLPGM PGM(QNTCSDK/MK_ACLS_P) SRCFILE(QNTCSDK/ACLS) <br>
<br>
3. Compile and link the CAPI sample &quot;acls&quot;:<br>
	CALL QNTCSDK/MK_ACLS_P<br>
 As a result, the command creates a C program acls (*PGM) in the library QNTCSDK&gt;<br>
<br>
<br>
<b><font size="5" color="#000080">Building C applications Using WebSphere Development Studio for iSeries CODE </font></b><br>
<br>
We will build a C program for the C API toolkit sample &quot;acls&quot; with the source code as an IFS file /qntcsdk/samples/admin/acls/acls.c.<br>
<br>
Start the CODE Program Generator.  This is typically in the Start Menu under Programs &gt; IBM WebSphere Development Studio Client for iSeries &gt; IBM CODE.  <br>

<ul type="disc">
<li><b>Compile the C API sample &quot;acls&quot; .</b></ul>
<br>
1.  From the Server pull-down menu, choose the server that contains the source code to be compiled.<br>
<br>
2.  In the Label menu, choose CRTCMOD.  After your selection, you should see &quot;CRTCMOD&quot; in the Command field, and &quot;ILE C Compile&quot; in the Associated Profile field. Also, the field name &quot;Source&quot; is displayed.<br>
<br>
3.  In the Source field, type in the full path name of the source file acls.c: &quot;/qntcsdk/samples/admin/acls/acls.c&quot;.<br>
<br>
4.  Click on the Options... button.  A window named &quot;Create C Module Compiler Options&quot; should pop up.  Now we specify the compiler options:<br>
<br>
a.  Under the Module tab, enter &quot;acls&quot; in the Module field.  In the Library field, enter &quot;qntcsdk&quot;.  Select the Source stream file checkbox.  You should see these options appear in the generated command at the bottom of the window.<br>
<br>
b.  Under the Generation tab, select &quot;*INHERIT&quot; for Storage model and &quot;*YES&quot; for the Teraspace storages addresses.  Leave everything else as the default.<br>
<br>
c.  Under the Debug tab, select &quot;*ALL&quot; for Debugger View. <br>
<br>
d.  Under the Other tab:
<ul type="disc">
<li>select &quot;*IFSIO&quot; for the Integrated File Systems options.  
<li>For Target CCSID, type in &quot;37&quot;.  
<li>For the Include Directory, type in &quot;/qibm/proddata/qadrt/include&quot; and click Add.  Then type in &quot;/qibm/proddata/lotus/notesapi/include&quot; and click Add again.  
<li>For Define preprocessor macros&quot;, add &quot;OS400&quot; and &quot;UNIX&quot;.</ul>
<br>
5. Check to see that the resulting command at the bottom of the window is:<br>
<br>
CRTCMOD  MODULE(qntcsdk/acls) SRCSTMF('&amp;I') TEXT(*SRCMBRTXT) OPTION(*EVENTF) STGMDL(*INHERIT) TERASPACE(*YES) DBGVIEW(*ALL) SYSIFCOPT(*IFSIO) TGTCCSID(37) INCDIR('/qibm/proddata/qadrt/include' '/qibm/proddata/lotus/notesapi/include') DEFINE(OS400 UNIX) <br>
<br>
   Click OK.  The pop-up window should go away.<br>
<br>
6. Click Submit.  You should get a message saying the command CRTCMOD has completed successfully.  If you check on the IBM i, you will see the module ACLS created in library QNTCSDK.<br>

<ul type="disc">
<li><b>Link the module QNTCSDK/ACLS into a program.</b></ul>
<br>
1.  From the Server pull-down menu, choose the server that contains the module to be linked in to a program.<br>
<br>
2.  In the Label menu, choose CRTPGM.  After your selection, you should see &quot;CRTPGM&quot; in the Command field, and &quot;ILE Bind&quot; in the Associated Profile field.  Also, the field name &quot;Program&quot; is displayed.<br>
<br>
3.  In the Program field, type in the program name in &quot;library-name/program-name&quot; format: &quot;qntcsdk/acls&quot;.<br>
<br>
4.  Click on the Options... button.  A window named &quot;Create Program Options&quot; should pop up.  Now we specify the bind options:<br>
<br>
a.  Under the Create Program tab, select &quot;*PGM&quot; for Module List&quot;.  In the Entry Module field, enter &quot;qadrtmain2&quot;.  In the Entry Library field, enter &quot;qadrt&quot;.  Leave everything else as the default.<br>
<br>
b.  Under the Bind Service Programs tab: for Bind service programs, add &quot;qnotes/libnotes&quot; and &quot;qadrt/qadrtts&quot;.  <br>
<br>
c.  Under the Other tab:
<ul type="disc">
<li>Select &quot;*DUPPROC&quot; for the Duplicate procedure names  
<li>Select &quot;*DUPVAR&quot; for the Duplicate variable names
<li>Select &quot;*BASIC&quot; for the Listing detail field</ul>
<br>
5. Check to see that the resulting command at the bottom of the window is:<br>
<br>
CRTPGM PGM(&amp;L/&amp;F) MODULE(*PGM) ENTMOD(qadrt/qadrtmain2) BNDSRVPGM(qnotes/libnotes qadrt/qadrtts) OPTION(*DUPPROC *DUPVAR) DETAIL(*BASIC)  <br>
<br>
    Click OK.  The pop-up window should go away.<br>
<br>
6. Click Submit.  You should get a message saying the command CRTPGM has completed successfully.  If you check on the IBM i, you will see the *PGM ACLS created in library QNTCSDK.
---
