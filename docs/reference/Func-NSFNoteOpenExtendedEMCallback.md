##### Function : Extension Manager
##### NSFNoteOpenExtendedEMCallback - Extension Manager callback for EM_NSFNOTEOPENEXTENDED
---
##### #include <extmgr.h>
STATUS LNPUBLIC **NSFNoteOpenExtendedEMCallback(**

	DBHANDLE  hDB,
	NOTEID  NoteID,
	DWORD  flags,
	DWORD  SinceSeqNum,
	BYTE *pKey,
	HANDLE *rtn);
**Description :**
EM_NSFNOTEOPENEXTENDED is a Notes internal, extended form of NSFNoteOpen and 
NSFNoteOpenExt.
**Parameters :**
Input :
hDB  -  The handle of the open database that contains the note.

NoteID  -  The ID of the note you want to open.

flags  -  Flags that control the manner in which the note is opened.  The flags are defined in OPEN_xxx (note) and may be or'ed together to combine functionality.

SinceSeqNum  -  This parameter is used to return only those items stored after it's sequence value and is used by the replicator.

pKey  -  This parameter is needed to open a link note stored by the mail router for single message store.

Output :
(routine)  -  
ERR_EM_CONTINUE


rtn  -  A handle to the open note.

**See Also :**
[EM_xxx](D:/md_files/EM_xxx.md)
---
