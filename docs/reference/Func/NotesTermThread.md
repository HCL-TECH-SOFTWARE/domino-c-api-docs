##### Function : Main Routines
##### NotesTermThread - Thread shutdown routine.
---
```
#include <global.h>
void LNPUBLIC NotesTermThread(
void);
```
**Description :**

Each thread that calls NotesInitThread() must also call NotesTermThread() 
before the thread terminates.  NotesTermThread() will free resources allocated 
by Domino or Notes for that thread.

**Parameters :**

Output :
(routine)  -  None.



**See Also :**
[NotesInitExtended](/domino-c-api-docs/reference/Func/NotesInitExtended)
[NotesTerm](/domino-c-api-docs/reference/Func/NotesTerm)
[NotesInitThread](/domino-c-api-docs/reference/Func/NotesInitThread)
---
