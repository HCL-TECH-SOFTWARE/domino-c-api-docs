##### Chapter 4-2
##### NotesMain versus Main

<b><font size="5" color="#000080">NotesMain</font></b><br>
<br>
The simplest way to structure a HCL C API character-based program for Domino and Notes is to write a subroutine named NotesMain as the entry point into the program. <br>
<br>
The HCL C API object file for Domino and Notes that is linked in contains the standard C entry point, main, which allows the program to run as a stand-alone<font color="#FF0000"> </font>application. This main initializes the Domino or Notes run-time system. It establishes a Domino or Notes session for the calling task, locates the Domino or Notes data directory, reads the notes.ini file, and finds the user ID file. It then calls NotesMain. If NotesMain returns an error code value other than NOERROR, main looks up the error message string associated with that error code, prints it to the screen, calls NotesTerm to do some cleanup, and exits.<br>
<br>
<br>
<b><font size="4" color="#000080">Command Line Arguments</font></b><br>
<br>
The main routine in the C API startup code passes the command line arguments (argc and argv) to NotesMain. <br>
<br>
<b><font size="4" color="#000080">Returning from NotesMain</font></b><br>
<br>
NotesMain is a subroutine that returns a value of type STATUS, which is defined in one of the C API header files. Many HCL C API functions for Domino and Notes return a STATUS value. A special STATUS value, NOERROR, is defined as zero in the C API, allowing C API programs to detect error conditions by checking to see if the STATUS value is logically TRUE.<br>
<br>
NotesMain should never call the exit function. Since NotesMain is a subroutine called from main, it should always return a value of type STATUS.<br>
<br>
<b><font size="5" color="#000080">main</font></b><br>
<br>
A C API program that uses the traditional C program entry point main must call NotesInitExtended to explicitly initialize the Domino or Notes run-time system before executing any C API functions. After finishing all calls to C API functions, it must call the function NotesTerm to terminate the Domino or Notes session.<br>
<br>
NotesInitExtended establishes a Domino or Notes session for the C API calling task. This function locates the Domino or Notes data directory, reads the notes.ini file, and finds the user ID file.  All other C API functions assume that a Domino or Notes session has already been established.<br>
<br>
C API programs that use the NotesMain entry point do not explicitly call NotesInitExtended or NotesTerm. Initialization and termination of the Domino or Notes session occurs automatically.<br>
<br>
<b><font size="4" color="#000080">Error Handling without NotesMain</font></b><br>
<br>
A C API program that uses main as the entry point can handle an error code returned by a C API function by printing an error string associated with the code, terminating the Lotus or Notes session, and terminating execution. Use the C API function OSLoadString to translate a C API error code of type STATUS into a printable string. Call NotesTerm to terminate the Domino or Notes session. Call the standard C function exit to terminate execution. <br>
<br>
Programs that use NotesMain do not need to convert error codes to strings. The Domino and Notes startup code linked into such programs automatically converts the error code returned by NotesMain to a string and prints it after NotesMain returns.<br>
<br>
<br>
<b><font size="5" color="#000080">Example Program</font></b><br>
<br>
The sample program, INTRO, uses the main entry point and explicitly calls NotesInitExtended to initialize the Domino run-time system. <br>
<br>
<b><font size="4" color="#000080">Opening and Closing Domino Databases</font></b><br>
<br>
After initializing the Domino or Notes run-time system, INTRO calls NSFDbOpen to open the specified database. <br>
<br>
NSFDbOpen requires the name of a Domino database file as input. If successful, NSFDbOpen yields a database handle. INTRO declares a variable of type DBHANDLE (a type defined in one of the C API include files) to store this handle.<br>
<br>
NSFDbOpen opens the database and initializes the database handle. Once you have initialized a database handle, use<font color="#FF0000"> </font>it for all subsequent access to the database. NSFDbClose closes the database and frees the memory object specified by the database handle. Always close any open databases before returning. Do not attempt to use a database handle after closing the database.<br>
<br>
<br>
<b><font size="4" color="#000080">Reading Domino Databases</font></b><br>
<br>
After opening the database, INTRO calls NSFDbInfoGet to retrieve information about the database. Notice that NSFDbInfoGet requires the handle of a Domino database as input. If successful, NSFDbInfoGet yields a string of information about the database as output. <br>
<br>
The length of the string returned by NSFDbInfoGet never exceeds NSF_INFO_SIZE, a constant value defined in one of the C API include files. INTRO defines an array of size NSF_INFO_SIZE to store this string. <br>
<br>
The string returned is a zero-terminated LMBCS string. INTRO calls the C run-time library function printf to print the information to the screen.<br>
<br>
<b><font size="5" color="#000080">Summary</font></b><br>
<br>
The following table summarizes the structural differences between a C API program that uses main as its entry point and one that uses NotesMain.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="50%">Structure of main</td><td width="50%">Structure of NotesMain</td></tr>

<tr valign="top"><td width="50%">main ()<br>
{<br>
 NotesInitExtended();<br>
 .<br>
 . body of the program<br>
 .<br>
 NotesTerm();<br>
 exit;<br>
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

---
