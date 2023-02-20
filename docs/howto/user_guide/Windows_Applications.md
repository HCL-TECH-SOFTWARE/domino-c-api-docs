##### Chapter 4-3
##### Windows Applications

<b><font size="5" color="#000080">NotesInitExtended and NotesTerm</font></b><br>
<br>
Like other Windows programs, a C API Windows application can use the Windows entry point WinMain. It must explicitly initialize the Domino or Notes-run time system before executing any C API functions. After finishing all calls to C API functions, it must terminate the Domino or Notes session. <br>
<br>
To explicitly initialize the Domino or Notes run-time system, call the function NotesInitExtended before entering the message dispatch loop. If NotesInitExtended returns an error code (a nonzero status value) the program should display an error message (for example, in a message box) and return before entering the message dispatch loop. If NotesInitExtended is successful, the program enters the message dispatch loop. When the loop terminates, call the function NotesTerm to terminate the Notes run-time system.<br>
<br>
NotesInitExtended establishes a Domino or Notes session for the calling task. It locates the Domino or Notes data directory, reads the notes.ini  file, and finds the user ID file. All other C API functions assume a Domino or Notes session has already been established successfully.<br>
<br>
C API programs that use NotesMain as the entry point do not explicitly call NotesInitExtended or NotesTerm. Initialization and termination of the Domino or Notes session occur automatically. Windows applications cannot use NotesMain because the startup code that calls NotesMain is character-based.<br>
<br>
The following table summarizes the structural differences between a C API program that uses WinMain as its entry point and one that uses NotesMain.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="50%">Structure of WinMain</td><td width="50%">Structure of NotesMain</td></tr>

<tr valign="top"><td width="50%">int PASCAL WinMain ()<br>
{<br>
 NotesInitExtended();<br>
 .<br>
 .<br>
 .<br>
 while(GetMessage(&amp;msg, ...))<br>
 .<br>
 .<br>
 .<br>
 NotesTerm();<br>
<br>
 return(msg.wParam);<br>
}</td><td width="50%">STATUS LNPUBLIC NotesMain ()<br>
{<br>
<br>
 .<br>
 . body of the program<br>
 .<br>
<br>
 return(NOERROR);<br>
}</td></tr>
</table>
<br>
<b><font size="5" color="#000080">Error Handling</font></b><br>
<br>
Windows C API applications can handle an error code returned by a C API function by displaying an error string associated with that code, performing any necessary error handling, and then returning control to Windows. The C API function OSLoadString translates a C API error code of type STATUS into a character string. <br>
<br>
Programs that use NotesMain do not need to convert error codes to strings. The Domino or Notes startup code linked into such programs automatically converts the error code returned by NotesMain to a string and prints it after NotesMain returns.<br>
<br>
<br>
<b><font size="5" color="#000080">Example Program</font></b><br>
<br>
For an example of a HCL C API for Domino and Notes Windows application, refer to the sample program INTROWIN. This program is a Windows version of the sample program, INTRO.<br>
<br>
<br>
<b><font size="4" color="#000080">The Main Window Procedure</font></b><br>
<br>
INTROWIN opens and processes a main window. The main window presents a menu (defined in file introwin.rc). The menu presents only one choice, File. The File menu presents two choices, Get Database Title or Quit.<br>
<br>
The Get Database Title choice causes a dialog box to appear that prompts for a database file name. Given the database file name, INTROWIN opens the specified database, reads the database title, and prints the database title in a message box on the screen. <br>
<br>
Note that INTROWIN uses the same C API functions to open a Domino database (NSFDbOpen), read the database title (NSFDbInfoGet), and close the database (NSFDbClose) as INTRO.  Most HCL C API functions for Domino and Notes work identically in all supported environments.<br>
<br>
<b><font size="4" color="#000080">Running INTROWIN</font></b><br>
<br>
Run INTROWIN from the Windows Program Manager by selecting File - Run. The Run dialog box appears. Type the fully qualified pathname of the executable in the &quot;command line&quot; edit field and click OK. The fully qualified path to the executable depends on your installation. For example, the command line may be:
<ul>
<ul><br>
	<tt>c:\notesapi\samples\basic\introwin\introwin.exe</tt><br>
</ul>
</ul>
If INTROWIN initializes successfully, the main program window appears. The window title is &quot;Intro Notes API Program&quot;. This window provides a File menu. <br>
<br>
Select File - Get Database Title. The Get Database Title dialog box appears. Type the file name of a Domino database in the Get Database Name edit field and click OK.<br>
<br>
If the Domino database file resides in the Domino or Notes data directory, you do not need to qualify the file name. If the file name ends with .nsf, you need not specify the extension. For example, if intro.nsf resides in the Domino or Notes data directory, type &quot;intro&quot; in the Get Database Name edit field.<br>
 <br>
After you click OK, a dialog box displays the title of the database. For example:<br>
<br>
<tt>		The title of this database is...</tt><br>
<br>
<tt>		API Test Database</tt><br>

---
