##### Function : Database
##### NSFDbSetObjectStoreID - Set the replica ID of a Domino Object Store in a Domino database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbSetObjectStoreID(**

	DBHANDLE  dbhandle,
	DBID far *ObjStoreReplicaID);
**Description :**
Store the specified replica ID for a Domino Object Store into the specified 
Domino database.  This creates an association between the database and the 
Object Store.
**Parameters :**
Input :
dbhandle  -  Handle of the Domino database to associate with the Domino Object Store.

ObjStoreReplicaID  -  Replica ID of the Domino Object Store.

Output :
(routine)  -  (routine)  -  Return status from this call -- indicates either success, or what the error is.  The return codes include:

NOERROR
ERR_IS_OBJSTORE - The replica ID for a Domino Object Store cannot be written into a Domino Object Store (only into a Domino database).


**See Also :**
[NSFDbCreateObjectStore](D:/md_files/NSFDbCreateObjectStore.md)
[NSFDbGetObjectStoreID](D:/md_files/NSFDbGetObjectStoreID.md)
---
