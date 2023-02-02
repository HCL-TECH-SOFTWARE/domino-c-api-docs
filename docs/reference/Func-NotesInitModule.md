##### Function : Main Routines
##### NotesInitModule - Return module handles used by Domino and Notes.
---
##### #include <global.h>
void LNPUBLIC **NotesInitModule(**

	HMODULE far *rethModule,
	HMODULE far *rethInstance,
	HMODULE far *rethPrevInstance);
**Description :**
This function returns the module handles for Domino and Notes.
**Parameters :**

Output :
rethModule  -  May be NULL.  If non-NULL, the module handle for the API application is stored at this address.

rethInstance  -  May be NULL.  If non-NULL, the instance handle for the API application is stored at this address.

rethPrevInstance  -  May be NULL.  If non-NULL, the handle for the previous instance of the API application is stored at this address.

**See Also :**
[NotesInitExtended](D:/md_files/NotesInitExtended.md)
---
