##### Function : Database
##### NSFDbCopy - Copies notes from one database to another.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbCopy(**

	DBHANDLE  hSrcDB,
	DBHANDLE  hDstDB,
	TIMEDATE  Since,
	WORD  NoteClassMask);
**Description :**
This function copies notes from one database to another.  You may specify two 
conditions that will filter which notes are copied: a cutoff time/date, and a 
NOTE_CLASS_xxx mask.

The Cutoff Date and Cutoff Interval (from the Replication Settings) are copied 
from the source database to the destination database along with the selected 
notes.

To create a replica copy of a database, use NSFDbCopyExtended with the Flag 
DBCOPY_REPLICA.

Please note that NSFDbCopy does not copy the ACL or the database information 
buffer to the destination database.  These operations can be completed using 
the appropriate Database API functions.
**Parameters :**
Input :
hSrcDB  -  The handle of the souce database.

hDstDB  -  The handle of the destination database.

Since  -  A TIMEDATE structure that specifies the earliest note that is copied.  To copy all notes, use TimeConstant() with the TimeConstantType argument set to TIMEDATE_WILDCARD.

NoteClassMask  -  The classes of notes that are copied.  Note classes are defined by the bit masks, NOTE_CLASS_xxx, and may be OR'ed together to copy more than one class of notes.

Output :
(routine)  -  Return status from this call -- indicates either success, or what the error is.  The return codes include:

NOERROR
ERR_NO_MODIFIED_NOTES


**Sample Usage :**
```

       /* if New DB from a template */
       if (error_status = NSFDbCopy(db_handle_src, db_handle_dst,
                              copy_cutoff_td, NOTE_CLASS_ALLNONDATA))
           goto Exit;
       if (error_status = NSFDbCopyTemplateACL(db_handle_src,
                              db_handle_dst, user_name,
                              ACL_LEVEL_MANAGER))
           goto Exit;
   }

```
**See Also :**
[NSFDbCopyACL](D:/md_files/NSFDbCopyACL.md)
[NSFDbCopyTemplateACL](D:/md_files/NSFDbCopyTemplateACL.md)
[NSFDbInfoGet](D:/md_files/NSFDbInfoGet.md)
[NSFDbInfoSet](D:/md_files/NSFDbInfoSet.md)
[NSFDbReplicaInfoGet](D:/md_files/NSFDbReplicaInfoGet.md)
[NSFDbReplicaInfoSet](D:/md_files/NSFDbReplicaInfoSet.md)
[NOTE_CLASS_xxx](D:/md_files/NOTE_CLASS_xxx.md)
---
