##### Function : Main Routines
##### NotesInitThread - Thread initialization routine
---
```
#include <global.h>
STATUS LNPUBLIC NotesInitThread(
void);
```
**Description :**

Initialize the Domino or Notes runtime system to support a new thread.  
Applications may makeC API calls from more than one thread.  Each new thread 
must call NotesInitThread() before making any other C API calls.

	The first thread calls NotesInitExtended which does the process 
initialization as well as the the initialization for that thread.  Each 
subsequent thread must call NotesInitThread and, before terminating, each 
subsequent thread must call NotesTermThread.  The last thread out must call 
NotesTerm.  However, the thread that calls NotesInitExtended does not have to 
be the thread that calls NotesTerm.

**Parameters :**

Output :
(routine)  -  NOERROR if successfull, or a non-zero return value if unable to initialize thread state.



**See Also :**
[NotesInitExtended](/domino-c-api-docs/reference/Func/NotesInitExtended)
[NotesTerm](/domino-c-api-docs/reference/Func/NotesTerm)
[NotesTermThread](/domino-c-api-docs/reference/Func/NotesTermThread)
---
