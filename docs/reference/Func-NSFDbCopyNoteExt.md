##### Function : Database
##### NSFDbCopyNoteExt - Copy a single note from one database to another.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbCopyNoteExt(**

	DBHANDLE  hSrcDB,
	DBID far *SrcDbID,
	DBID far *SrcReplicaID,
	NOTEID  SrcNoteID,
	DBHANDLE  hDstDB,
	DBID far *DstDbID,
	DBID far *DstReplicaID,
	DWORD  dwOpenFlags,
	DWORD  dwUpdateFlags,
	NOTEID far *retDstNoteID,
	WORD far *retNoteClass);
**Description :**
This function copies a single note from a source database to the destination 
database.  This routine detects if the source and destination databases are 
replicas of each other, and sets ID information in reference items in notes 
appropriately.  This routine is similar to NSFDbCopyNote, but it also allows 
you to specify flags that control the manner in which the source note is opened 
and flags which specify how the destination note is updated. This function 
allows using extended 32-bit DWORD update options, as described in the entries 
OPEN_xxx and UPDATE_xxx.
**Parameters :**
Input :
hSrcDB  -  A database handle to the source database.

SrcDbID  -  Not used.  Pass NULL for this parameter.

SrcReplicaID  -  Optional.  A pointer to the replica ID (also a DBID) of the source database.  NULL may be used for this pointer.  If you pass in NULL for this value, SrcReplicaID will be determined by using the hSrcDb.  Pass in a pointer to the replica ID of the source database, if you happen to already have the ID, to optimize this call.

SrcNoteID  -  The NOTEID of the source note.

hDstDB  -  A database handle to the destination database.

DstDbID  -  Not used.  Pass NULL for this parameter.

DstReplicaID  -  Optional.  A pointer to the replica ID (also a DBID) of the destination database.  NULL may be used for this pointer.

dwOpenFlags  -  Flags that control the manner in which the source note is opened. This, in turn, controls what information about the note is available to you and how it is structured. The flags are defined in OPEN_xxx (note) and may be or'ed together to combine functionality.

dwUpdateFlags  -  Flags that control the manner in which the destination note is updated. The flags are defined in UPDATE_xxx and may be or'ed together to combine functionality.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully copied note to destination database.
ERR_NOTE_DELETED - Document has been deleted.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retDstNoteID  -  Optional.  The address of a NOTEID in which the Note ID of the newly copied note is returned.  Use NULL if you do not need this returned information.  If the Note copy is created in a non-replica database, a new Originator ID (OID) will be generated, so that the copy appears as a unique new note in the destination database.

retNoteClass  -  Optional.  The address of a WORD in which the NOTE_CLASS_xxx of the copy is returned.  Use NULL if you do not need this returned information.

**See Also :**
[NSFDbCopy](D:/md_files/NSFDbCopy.md)
[NSFDbCopyNote](D:/md_files/NSFDbCopyNote.md)
[NSFDbIDGet](D:/md_files/NSFDbIDGet.md)
[OPEN_xxx (note)](D:/md_files/OPEN_xxx (note).md)
[UPDATE_xxx](D:/md_files/UPDATE_xxx.md)
---
