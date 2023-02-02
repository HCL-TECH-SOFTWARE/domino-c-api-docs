##### Function : Database
##### NSFDbGetNoteInfoByUNID - Get  information from a note's on-disk header.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbGetNoteInfoByUNID(**

	DBHANDLE  hDB,
	UNID far *pUNID,
	NOTEID far *retNoteID,
	OID far *retOID,
	TIMEDATE far *retModTime,
	WORD far *retClass);
**Description :**
This function takes a database handle and Universal Note ID.  It returns the 
note id, the note's Originator ID (OID) structure, the time and date the note 
was last modified, and the NOTE_CLASS_xxx. 
**Parameters :**
Input :
hDB  -  A handle to an open Domino database.

pUNID  -  The Universal Note ID.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully retrieved the note information.

ERR_NOTE_DELETED - Document has been deleted.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retNoteID  -  (Optional)  Pointer to the returned note id;  may be NULL.

retOID  -  (Optional)  Pointer to the returned populated ORIGINATORID (OID) structure containing the database creation time/date, note creation time/date, note sequence number, and the sequence time/date (when added to database).  May be NULL.

retModTime  -  (Optional)  Pointer to the returned populated TIMEDATE structure containing the note's last modified time and date normalized to Greenwich Mean Time (GMT).  May be NULL.

retClass  -  (Optional)  Pointer to the returned NOTE_CLASS_xxx (type of note);  may be NULL.

**See Also :**
[NSFDbGetNoteInfo](D:/md_files/NSFDbGetNoteInfo.md)
---
