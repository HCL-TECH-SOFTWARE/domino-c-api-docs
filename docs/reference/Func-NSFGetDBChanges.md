##### Function : Database
##### NSFGetDBChanges - Get the database changes that have occurred on the server since SinceTime
---
##### #include <nsfdb.h>
STATUS far PASCAL **NSFGetDBChanges(**

	char *pServerName,
	TIMEDATE *SinceTime,
	DWORD  DbListSize,
	MEMHANDLE  hDbList,
	DWORD  ListFlags,
	DWORD  Flags,
	DWORD *retChangesSize,
	MEMHANDLE *rethChanges,
	TIMEDATE *retNextSinceTime);
**Description :**
Get the database changes that have occurred on the server since SinceTime
**Parameters :**
Input :
pServerName  -  name of server to check for db changes on (failover will not happen with this API)

SinceTime  -  list of dbs located in rethChanges will only be populated with dbs that have been modified since this time 

DbListSize  -  Size of the memory of hDbList 

hDbList  -  Optional handle to a null-terminated list of databases you want info on. If NULL, any database on the server can potentially be returned back.  If not null, only the databases in this list have the potential to be listed in the returned rethChanges

ListFlags  -  Attributes to receive back in rethChanges.  If NULL, rethChanges will only pass back a list of dbname strings
 		GETCHANGES_TDDATAMODIFIED     - time of last data modification to db
 		GETCHANGES_TDNONDATEMODIFIED  - time of last non-data modification to db (creating a new folder etc.)
 		GETCHANGES_TDFOLDERMODIFIED   - time of last folder modification to db (moves to folder etc.)
 		GETCHANGES_TDUNREADMODIFIED   - time of last change of read/unread list on db

Flags  -  Reserved, must be 0

Output :
(routine)  -  NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


retChangesSize  -  Size in bytes of the value represented by rethChanges

rethChanges  -  Returned list of dbs that have changed since SinceTime. Each list entry contains a null-terminated database path and a sequence of TIMEDATE values corresponding to the ListFlags parameter.  Attributes that aren't listed in Listflags won't be sent. 
Note: The relative path of the changed dbs will not be localized for you automatically.  For instance, you may see a forward-slash vs a back-slash depending on what Operating System pServerName is.
For example:
       "mail/FakeMailBox.nsf" <TIMEDATE DataModified> <TIMEDATE NonDataModified> <TIMEDATE FolderModified> <TIMEDATE UnreadModified>
       "mail/AnotherMailBox.nsf" <TIMEDATE DataModified> <TIMEDATE NonDataModified> <TIMEDATE FolderModified> <TIMEDATE UnreadModified> 


retNextSinceTime  -  New Since Time

**See Also :**
[](D:/md_files/.md)
---
