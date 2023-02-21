##### Function : Clusters
##### NSFDbCreateAndCopy - Creates a new copy of a database based on the original.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCreateAndCopy(

	const char far *srcDb,
	const char far *dstDb,
	WORD  NoteClass,
	WORD  limit,
	DWORD  flags,
	DBHANDLE far *retHandle);
```
**Description :**

This function creates a new copy of a Domino database based on the one supplied 
in SrcPathName.  The database class of the new database is based on the file 
extension specified by SrcPathName.  Specifically, the new copy will contain 
the replication settings, database options, Access Control List, Full Text 
Index (if any),  as well as data and non-data notes (dependent on the NoteClass 
argument) of  the original database. 

You may specify the types of notes that you want copied to the new database 
with the NoteClass argument.  You may also specify the maximum size (database 
quota) that the database can grow to (in megabytes) with the Limit argument.  
Additionally, you may specify that the new database is to be a replica copy of 
the original database, meaning that it will share the same replica ID.  If 
successful, this function will return a handle to the newly created Domino 
database in rethDB.  The handle can then be used in other C API functions that 
accept a DBHANDLE as input.  You will need to call NSFDbClose to close the 
newly created database when done with the handle.

If the source database is a replica copy that has not yet been initialized or 
the replication settings in the source database are set to never replicate,  
then a new copy will not be permitted if the DBCOPY_REPLICA flag is set.

Note:  NFSDbCreateAndCopy will return the error ERR_NOACCESS if the source 
database is located on a server and contains private design elements (view, 
folder, etc...) not owned by the current user and the NOTE_CLASS_PRIVATE flag 
is not cleared in the NoteClass argument.

**Parameters :**
Input :
srcDb  -  A fully qualified pathname of the source database.

dstDb  -  A fully qualified pathname of the destination database.

NoteClass  -  Class of notes to be copied.  This field may specify more than one NoteClass by passing a Bitwise OR of NOTE_CLASS constants.

limit  -  Size limit for new database.  Specified in megabytes (e.g. a value of 1 indicates size limit of 1 MB).  This argument will control how large the new copy can grow to.  Specify a value of zero if you do not wish to place a size limit on the newly copied database.

flags  -  Option flags determining type of copy.  Currently, the only supported flags are DBCOPY_REPLICA, , DBCOPY_ENCRYPT_SIMPLE, DBCOPY_ENCRYPT_MEDIUM, DBCOPY_ENCRYPT_STRONG, DBCOPY_REPLICA_NAMELIST, DBCOPY_DEST_IS_NSF, DBCOPY_DEST_IS_DB2, and DBCOPY_OVERRIDE_DEST.

If the DBCOPY_REPLICA flag is set then the newly copied database will be a replica copy of the original database.  If the DBCOPY_REPLICA flag is not set then the new copy will have a unique replica ID.

Output :
(routine)  -  If successful,  returns NOERROR; otherwise, returns database access errors.


retHandle  -  Address of location to store handle to newly created database.


**Sample Usage :**
```
#include <nsfdb.h>

STATUS error;
DBHANDLE hNewDb = NULLHANDLE;
DBHANDLE hRepDb = NULLHANDLE;
DBHANDLE hCopyDb = NULLHANDLE;
char template[MAXPATH] = "template.ntf";
char newdb[MAXPATH] = "new.nsf";
char repdb[MAXPATH] = "replica.nsf";
char copydb[MAXPATH] = "copy.nsf";
	 
/* create a database based on a template */
error = NSFDbCreateAndCopy(template, newdb, NOTE_CLASS_ALLNONDATA, 0, 0, 
&hNewDb);

/* create a replica of the first database */
error = NSFDbCreateAndCopy(newdb, repdb, NOTE_CLASS_ALL, 0, DBCOPY_REPLICA,  
&hRepDb);

/* create a copy (not a replica) of the first database */
error = NSFDbCreateAndCopy(newdb, copydb, NOTE_CLASS_ALL, 0, 0, &hCopyDb);
```
**See Also :**
[NOTE_CLASS_xxx](/domino-c-api-docs/reference/Symb/NOTE_CLASS_xxx)
---
