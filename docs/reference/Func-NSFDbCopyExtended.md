##### Function : Database
##### NSFDbCopyExtended - Copies notes from one database to another.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbCopyExtended(**

	DBHANDLE  hSrcDB,
	DBHANDLE  hDstDB,
	TIMEDATE  Since,
	WORD  NoteClassMask,
	DWORD  Flags,
	TIMEDATE far *retUntil);
**Description :**
This function copies notes from one database to another.  You may specify two 
conditions that will filter which notes are copied: a cutoff time/date, and a 
NOTE_CLASS_xxx mask.  In addition, flag values may be used to control 
additional options (the flags are described in the entry DBCOPY_xxx).

The Cutoff Date and Cutoff Interval (from the Replication Settings) are copied 
from the source database to the destination database along with the selected 
notes.

The TIMEDATE of the most recent note copied may be obtained by supplying a 
pointer to a TIMEDATE in the argument retUntil.  This argument is optional;  
pass NULL if this result is not wanted.

If the two databases are replicas, the notes copied will appear as replicas.  
If the databases are not replicas, the notes copied will appear as new notes in 
the destination database.

**Parameters :**
Input :
hSrcDB  -  The handle of the souce database.

hDstDB  -  The handle of the destination database.

Since  -  A TIMEDATE structure that specifies the earliest note that is copied.  To copy all notes, use TimeConstant() with the TimeConstantType argument set to TIMEDATE_WILDCARD.

NoteClassMask  -  The classes of notes that are copied.  Note classes are defined by the bit masks, NOTE_CLASS_xxx, and may be OR'ed together to copy more than one class of notes.

Flags  -  Option flags (see DBCOPY_xxx).  DBCOPY_DEST_IS_NSF, DBCOPY_DEST_IS_DB2, and DBCOPY_OVERRIDE_DEST are not supported.

Output :
(routine)  -  Return status from this call -- indicates either success, or what the error is.  The return codes include:

NOERROR
ERR_NO_MODIFIED_NOTES


retUntil  -  Optional;  if not NULL, the TIMEDATE of the most recent note copied is stored at this address.

**See Also :**
[NSFDbCopy](D:/md_files/NSFDbCopy.md)
[DBCOPY_xxx](D:/md_files/DBCOPY_xxx.md)
[NOTE_CLASS_xxx](D:/md_files/NOTE_CLASS_xxx.md)
---
