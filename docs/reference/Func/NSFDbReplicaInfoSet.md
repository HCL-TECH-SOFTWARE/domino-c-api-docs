##### Function : Database
##### NSFDbReplicaInfoSet - Set the database's DBREPLICAINFO structure.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbReplicaInfoSet(

	DBHANDLE  hDB,
	DBREPLICAINFO far *ReplicationInfo);
```
**Description :**

This function sets the given database's DBREPLICAINFO structure.

Use this function to set specific values, such as the replica ID, in the header 
data of a database.  To create a new replica copy of a given database, for 
example, you must first create the new database using the NSFDbCreate, then get 
the replica ID of the source database via NSFDbReplicaInfoGet, then set this 
replica ID into the new database via NSFDbReplicaInfoSet.

You may also use NSFDbReplicaInfoSet to set values such as the replication 
flags in the header of the database.  See the symbolic value REPLFLG_xxx for 
specific replication settings.

**Parameters :**
Input :
hDB  -  DBHANDLE obtained from a call to NSFDbOpen or NSFDbOpenExtended.

ReplicationInfo  -  A pointer to a DBREPLICAINFO structure that contains the database's new Replica ID, Purge Interval, Cutoff Date, and Replica flags.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully set replica information.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**Sample Usage :**
```
 
   /* Cast the changes in stone */
 
  if (error_status = NSFDbReplicaInfoSet(db_handle_dst,
                                          &replica_info_dst))
       goto Exit;

```
**See Also :**
[NSFDbReplicaInfoGet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoGet)
---
