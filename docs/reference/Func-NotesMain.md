##### Function : Main Routines
##### NotesMain - Entry point for character mode API programs.
---
##### #include <global.h>
STATUS LNPUBLIC **NotesMain(**

	int  argc,
	char far *argv[]);
**Description :**
Simplified entry point for character mode API programs. You may structure your 
API program as a function named NotesMain(). This causes the Domino or Notes 
run time system to be initialized automatically before your NotesMain function 
gets control. After your NotesMain function returns, the Domino or Notes run 
time system is automatically terminated. Therefore, your NotesMain function 
does not need to initialize or terminate the Domino or Notes run time system 
explicitly.

If you structure your API program as a NotesMain function, you must link your 
program with the Domino or Notes bootstrap object file.  Under Unix this object 
file is named notes0.o. Under Windows this file is named notes0.obj. The C API 
toolkit provides bootstrap object files for each platform in the LIB 
subdirectory appropriate to each platform.

Starting with Release 4.6, the argument strings passed to NotesMain() are 
translated to LMBCS, the Lotus Multi-Byte Character Set.
**Parameters :**
Input :
argc  -  Number of arguments passed to NotesMain.

argv[]  -  An array of pointers to the values of arguments passed to NotesMain.  Note that these pointers are in the current memory model, the same as arguments to "main".  The argument strings are translated to LMBCS before being passed to NotesMain().

Output :
(routine)  -  Returns -  status used by the Domino or Notes system. 

NOERROR - No error occurred causing or during termination of the C API program.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network problems,  etc.).  There are many possible problems from which your application will be incapable or unable to recover, so that this code should be saved during the debugging process.

As an additional error reporting aid, the NotesMain caller will translate the numeric value of anything other than NOERROR into the corresponding error string and  to report it to the console.


**Sample Usage :**
```
STATUS LNPUBLIC NotesMain (int argc, char *argv[])
{
    STATUS  error;
    char   *szDBName;
    DBHANDLE  hDB;

    szDBName = argv[1];

    error = NSFDbOpen(szDBName, &hDB);
    NSFDbClose(hDB);

    return( ERR(error));
}
```
**See Also :**
[AddInMain](D:/md_files/AddInMain.md)
[NotesInitExtended](D:/md_files/NotesInitExtended.md)
[NotesTerm](D:/md_files/NotesTerm.md)
---
