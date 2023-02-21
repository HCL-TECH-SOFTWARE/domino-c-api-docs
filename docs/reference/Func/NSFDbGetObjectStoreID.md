##### Function : Database
##### NSFDbGetObjectStoreID - Get the replica ID of a Note Object Store.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetObjectStoreID(

	DBHANDLE  dbhandle,
	BOOL far *Specified,
	DBID far *ObjStoreReplicaID);
```
**Description :**

If a Note Object Store is associated with this database, return the replica ID 
for the object store.

**Parameters :**
Input :
dbhandle  -  Handle of the database.

Output :
(routine)  -  (routine)  -  Return status from this call -- indicates either success, or what the error is.  The return codes include:

NOERROR



Specified  -  If a Note Object Store is associated with this database, this value is set to TRUE.

ObjStoreReplicaID  -  If a Note Object Store is associated with this database, the replica ID of the object store is placed at this address.


**See Also :**
[NSFDbCreateObjectStore](/domino-c-api-docs/reference/Func/NSFDbCreateObjectStore)
[NSFDbSetObjectStoreID](/domino-c-api-docs/reference/Func/NSFDbSetObjectStoreID)
---
