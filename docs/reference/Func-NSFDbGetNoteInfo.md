##### Function : Database
##### NSFDbGetNoteInfo - Get  information from a note's on-disk header.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbGetNoteInfo(**

	DBHANDLE  hDb,
	NOTEID  NoteID,
	OID far *retNoteOID,
	TIMEDATE far *retModified,
	WORD far *retNoteClass);
**Description :**
This function takes a database handle and note ID.  It returns the note's the 
Originator ID (OID) structure, the time and date the note was last modified, 
and the NOTE_CLASS_xxx.  It is the database level equivalent of three calls to 
NSFNoteGetInfo(), but requires a disk I/O or network I/O to obtain the 
information (and thus, it is fairly expensive to use).
**Parameters :**
Input :
hDb  -  A handle to an open Domino database.

NoteID  -  The NOTEID of the note whose particulars you wish to retrieve.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully retrieved the note information.

ERR_NOTE_DELETED - Document has been deleted.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retNoteOID  -  Returns the populated ORIGINATORID (OID) structure containing the database creation time/date, note creation time/date, note sequence number, and the sequence time/date (when added to database). 

retModified  -  Returns the populated TIMEDATE structure containing the note's last modified time and date normalized to Greenwich Mean Time (GMT).  

retNoteClass  -  Returns  pointer to NOTE_CLASS_xxx in a WORD, value indicates the type of note.  

**Sample Usage :**
```
  
   /* Find some SPECIAL notes: Policy and then designer's Help */
   
   if (error_status = NSFDbGetSpecialNoteID(db_handle_src,
                          SPECIAL_ID_NOTE | NOTE_CLASS_INFO,
                          &policy_nid_src))
   {
       if (ERR(error_status) == ERR_SPECIAL_ID)
           printf("\n%s has no Policy Note\n", src_name);
       else
           goto Exit;
   }
   else
   {
       if (error_status = NSFDbGetNoteInfo(db_handle_src,
                                           policy_nid_src,
                                           &policy_oid_src,
                                           &policy_lastmod_td,
                                           &policy_noteclass))
           goto Exit;
       printf("Policy Note ID = %08lX\n", policy_oid_src.Note);
   }

```
**See Also :**
[NSFDbOpen](D:/md_files/NSFDbOpen.md)
[NSFDbOpenExtended](D:/md_files/NSFDbOpenExtended.md)
[NSFDbGetSpecialNoteID](D:/md_files/NSFDbGetSpecialNoteID.md)
[NSFDbGetNoteInfoByUNID](D:/md_files/NSFDbGetNoteInfoByUNID.md)
[NSFNoteGetInfo](D:/md_files/NSFNoteGetInfo.md)
---
