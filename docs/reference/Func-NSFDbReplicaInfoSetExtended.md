##### Function : Database
##### NSFDbReplicaInfoSetExtended - Set the database's DBREPLICAINFO structure.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbReplicaInfoSetExtended(**

	DBHANDLE  hDB,
	DBREPLICAINFO far *ReplicationInfo,
	DHANDLE  hNamesList);
**Description :**
This function sets the given database's DBREPLICAINFO structure and allows for 
a NAMES_LIST structure UserName to provide authentication for trusted servers.

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

hNamesList  -  May be NULLHANDLE or a HANDLE to a NAMES_LIST structure that contains a UserName that is used to provide authentication for trusted servers.  This causes the UserName's ACL permissions in the database to be enforced.  Please see NSFBuildNamesList for more information on building a NAMES_LIST structure.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully set replica information.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


**See Also :**
[NSFDbReplicaInfoGet](D:/md_files/NSFDbReplicaInfoGet.md)
---
