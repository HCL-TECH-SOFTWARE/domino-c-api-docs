##### Function : Database
##### NSFDbReplicaInfoGet - Get the database's DBREPLICAINFO structure.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbReplicaInfoGet(

	DBHANDLE  hDB,
	DBREPLICAINFO far *retReplicationInfo);
```
**Description :**

This function gets the given database's DBREPLICAINFO structure.   This 
structure contains information that tells the Domino Replicator how to treat 
the database.

The ".ID" member enables the Replicator to identify "replicas" of databases.

The ".CutoffInterval" is the age in days at which deleted document identifiers 
are purged.  Domino divides this interval into thirds, and for each third of 
the interval carries out what amounts to an incremental purge.  These deleted 
document identifiers are sometimes called deletion stubs.

The ".Cutoff" member is a TIMEDATE value that is calculated by subtracting the 
Cutoff Interval (also called Purge Interval) from today's date.  It prevents 
notes that are older than that date from being replicated at all.

The ".Flags" member is a bit-wise encoded WORD that stores miscellaneous 
Replicator flags.  See REPLFLG_xxx for further information on Replicator flags.

**Parameters :**
Input :
hDB  -  DBHANDLE obtained from a call to NSFDbOpen or NSFDbOpenExtended.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully got replica information.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retReplicationInfo  -  The address of a DBREPLICAINFO structure in which the database's Replica ID, Purge Interval, Cutoff Date, and Replica flags will be returned.


**Sample Usage :**
```

   /* Copy Replica info and provide new Replica ID as required. */
 
  if (error_status = NSFDbReplicaInfoGet(db_handle_src,
                                          &replica_info_src))
       goto Exit;

```
**See Also :**
[NSFDbReplicaInfoSet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoSet)
---
