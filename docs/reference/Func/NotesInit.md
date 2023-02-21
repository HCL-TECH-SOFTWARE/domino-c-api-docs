##### Function : Main Routines
##### NotesInit - * OBSOLETE * Notes runtime initialization routine.
---
```
#include <global.h>
STATUS LNPUBLIC NotesInit(
void);
```
**Description :**

NotesInit() is obsolete;  this function has been replaced by 
NotesInitExtended().  NotesInit() is supported under OS/2 and Windows for 
backwards compatibility.  API programs that run under other operating systems, 
such as Unix, and use main() as the entry point, should call 
NotesInitExtended() rather than NotesInit(). 

If your program uses NotesInit(), then after all your program's Notes API calls 
have returned, but before your program exits, call NotesTerm().

NotesInit() locates the Notes program and Notes data directories and reads the 
notes.ini file. NotesInit() returns an error (a non-zero status) if, for 
example, Notes is not installed.

**Parameters :**

Output :
(routine)  -  A non-zero return value indicates that the Notes runtime did not initialize properly.



**See Also :**
[AddInMain](/domino-c-api-docs/reference/Func/AddInMain)
[NotesInitExtended](/domino-c-api-docs/reference/Func/NotesInitExtended)
[NotesInitThread](/domino-c-api-docs/reference/Func/NotesInitThread)
[NotesMain](/domino-c-api-docs/reference/Func/NotesMain)
[NotesTerm](/domino-c-api-docs/reference/Func/NotesTerm)
[NotesTermThread](/domino-c-api-docs/reference/Func/NotesTermThread)
---
