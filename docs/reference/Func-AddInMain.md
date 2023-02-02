##### Function : Main Routines
##### AddInMain - Entry point for IBM Domino Server Add-in API programs.
---
##### #include <addin.h>
STATUS LNPUBLIC **AddInMain(**

	HMODULE  hModule,
	int  argc,
	char far *argv[]);
**Description :**
Simplified entry point for IBM Domino Server add-in task API programs.  If an 
API program is a IBM Domino Server add-in task, it is recommended that 
AddInMain() be used as the main entry point.  Otherwise, the program must 
initialize the Domino run time system, call AddInCreateStatusLine() to create 
the IBM Domino Server's status line for this program, and call 
AddInDeleteStatusLine() before termination and terminate the Domino run time 
system.

API programs structured as AddInMain() functions must link with the two IBM C 
API for Domino and Notes bootstrap object files. Under Unix these object files 
are named notes0.o and notesai0.o. Under Windows these files are named 
notes0.obj and notesai0.obj . The C API toolkit provides these bootstrap object 
files for each platform in the LIB subdirectory appropriate to each platform.

Structuring an API program as an AddInMain() causes the Domino run time system 
to be initialized and a server add-in task control block to be initialized 
automatically before your AddInMain() function gets control. After AddInMain() 
returns, Domino automatically frees the add-in task control block. Therefore, 
AddInMain() functions do not initialize or terminate the Domino run time system 
explicitly.

The following paragraphs summarize the startup, execution, and shutdown of IBM 
Domino Server add-in tasks.

When a IBM Domino Server add-in task is loaded, several functions that were 
built into the executable, are invoked by the bootstrap code. These functions 
take care of network and server task initialization.  When those steps are 
completed, main() calls your AddInMain() and passes to it the module handle of 
the add-in task and any command line arguments.

The main control loop of an AddInMain() task code must be structured so that 
the loop terminates if either the AddInIdle() or AddInShouldTerminate() 
functions return TRUE.  When the IBM Domino Server administrator enters 'Quit' 
at the server console, either function will return TRUE any time it is called 
by your code.  When your code returns to its caller, the main() routine that 
was built around your AddInMain() cleans up any network operations, releases 
any resources allocated to your task, and terminates the process.  During 
server shutdown, all tasks are sequentially asked to perform their task 
shutdown obligations.  If your add-in task does not terminate in response to 
this protocol, the IBM Domino Server will appear to hang, but the IBM Domino 
Server is merely waiting for your add-in to finish whatever it is doing and 
terminate itself.

Under Windows, a string table resource is normally built into the add-in 
executable file.  By convention, the first two(2) entries in this string table 
must be:

PKG_ADDIN+0,  "{Application Name}"
PKG_ADDIN+1,  "{Application Version}"

Starting with Release 4.6, the arguments passed to AddInMain() are translated 
to LMBCS, the Lotus Multi-Byte Character Set.
**Parameters :**
Input :
hModule  -  A HMODULE containing the module handle of the AddInMain() executable.  This value is used to obtain resource strings using the OSLoadString() and LogAddText() APIs.

argc  -  An int containing the number of arguments on the command line, including one for the program name itself.

argv[]  -  The address of an array of pointers to LMBCS strings terminated by the NUL character ('\0').  One string is provided for each command line argument.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - No error occurred causing or during termination of the Server Add-in Task

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network,  etc.).


**See Also :**
[AddInIdle](D:/md_files/AddInIdle.md)
[AddInShouldTerminate](D:/md_files/AddInShouldTerminate.md)
[NotesInit](D:/md_files/NotesInit.md)
[NotesInitExtended](D:/md_files/NotesInitExtended.md)
[NotesMain](D:/md_files/NotesMain.md)
[NotesTerm](D:/md_files/NotesTerm.md)
---
