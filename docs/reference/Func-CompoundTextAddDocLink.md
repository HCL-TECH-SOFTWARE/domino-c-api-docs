##### Function : Compound Text
##### CompoundTextAddDocLink - Inserts a DocLink in a CompoundText context
---
##### #include <easycd.h>
STATUS LNPUBLIC **CompoundTextAddDocLink(**

	DHANDLE  hCompound,
	TIMEDATE  DBReplicaID,
	UNID  ViewUNID,
	UNID  NoteUNID,
	char far *pszComment,
	DWORD  dwFlags);
**Description :**
This function inserts a DocLink in a CompoundText context.
**Parameters :**
Input :
hCompound  -  Handle to the CompoundText context.

DBReplicaID  -  Replica ID of the database that contains the note (document) pointed to by the DocLink.

ViewUNID  -  UNID of the view that contains the note (document) pointed to by the DocLink.

NoteUNID  -  UNID of the note (document) pointed to by the DocLink.

pszComment  -  Pointer to a NULL terminated string.  This string appears when the DocLink is selected (clicked on).

dwFlags  -  Flags reserved for future use.  Set this parameter to 0L.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully added the DocLink to the CompoundText context.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**See Also :**
[CDLINK2](D:/md_files/CDLINK2.md)
[CDLINKEXPORT2](D:/md_files/CDLINKEXPORT2.md)
[NOTELINK](D:/md_files/NOTELINK.md)
---
