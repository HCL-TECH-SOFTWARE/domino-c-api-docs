##### Function : Database
##### NSFDbGenerateOID - Create new Originator ID for note in database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbGenerateOID(**

	DBHANDLE  hDB,
	OID far *retOID);
**Description :**
This function generates a new Originator ID (OID) used to uniquely identify a 
note.  Use this function when you already have a note open and wish to create a 
totally new note with the same items as the open note.  This function is 
commonly used after NSFNoteCopy, because the copy created by NSFNoteCopy has 
the same OID as the source note.

You do not need NSFDbGenerateOID when creating a new note from scratch using 
NSFNoteCreate, because NSFNoteCreate performs this function for you.

If the database resides on a remote Lotus Domino Server, the current user must 
to have the appropriate level of access to carry out this operation.
**Parameters :**
Input :
hDB  -  A handle to a Domino database.  

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully generated a new Originator ID.
ERR_NTCREATE_LICENSE - Cannot create a document without a valid user license.


retOID  -  The address of an OID structure in which the new OID will be returned.

**Sample Usage :**
```

   /* Update Note Info as if a delete & an add had taken place      */
 
  if (error_status = NSFDbGenerateOID(db_handle_dst, &new_oid))
       goto Exit;
   NSFNoteSetInfo(note_handle, _NOTE_OID, &new_oid);

```
**See Also :**
[NSFNoteGetInfo](D:/md_files/NSFNoteGetInfo.md)
[NSFNoteSetInfo](D:/md_files/NSFNoteSetInfo.md)
[NSFNoteUpdate](D:/md_files/NSFNoteUpdate.md)
[_NOTE_xxx](D:/md_files/_NOTE_xxx.md)
---
