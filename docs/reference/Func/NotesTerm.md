##### Function : Main Routines
##### NotesTerm - Domino and Notes runtime shutdown routine.
---
```
#include <global.h>
void LNPUBLIC NotesTerm(
void);
```
**Description :**

This routine is used only in programs that do NOT have a NotesMain() or 
AddinMain().

	A call to this routine will shut down the Domino or Notes runtime 
system.  Other Lotus C API functions for Domino and Notes cannot be used after 
calling this routine. 

	It is strongly suggested that applications terminate immediately after 
calling NotesTerm.   Failing to do so, applications can hold onto resources 
which cannot be easily cleaned up in the event of a Notes/Domino crash.

**Parameters :**

Output :
(routine)  -  None.



**See Also :**
[AddInMain](/reference/Func/AddInMain)
[NotesInit](/reference/Func/NotesInit)
[NotesInitExtended](/reference/Func/NotesInitExtended)
[NotesInitIni](/reference/Func/NotesInitIni)
[NotesMain](/reference/Func/NotesMain)
---
