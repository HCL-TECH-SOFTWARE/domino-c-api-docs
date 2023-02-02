##### Function : Main Routines
##### NotesTerm - Domino and Notes runtime shutdown routine.
---
##### #include <global.h>
void LNPUBLIC **NotesTerm(**
void);
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
[AddInMain](D:/md_files/AddInMain.md)
[NotesInit](D:/md_files/NotesInit.md)
[NotesInitExtended](D:/md_files/NotesInitExtended.md)
[NotesInitIni](D:/md_files/NotesInitIni.md)
[NotesMain](D:/md_files/NotesMain.md)
---
