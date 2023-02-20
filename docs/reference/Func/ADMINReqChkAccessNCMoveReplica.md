##### Function : Administration Process
##### ADMINReqChkAccessNCMoveReplica - Create a "Check Access for Non-cluster Move Replica Creation" request. 
---
```
#include <adminp.h>
STATUS LNPUBLIC ADMINReqChkAccessNCMoveReplica(

	DBHANDLE  dbhAdmin4,
	char far *chAuthor,
	char far *chSrcServer,
	char far *chSrcPathName,
	char far *chTitle,
	DBREPLICAINFO *Replicainfo,
	char far *chDesServer,
	char far *chDesPathName,
	ADMINReqParams far *arpAdminReqParamsPtr,
	WORD  wAdminReqParamsSize);
```
**Description :**

This function creates a "Check Access for Non-cluster Move Replica Creation" 
request in the Administration Requests database (admin4.nsf). 

**Parameters :**
Input :
dbhAdmin4  -  Handle of the Administration Request database (admin4.nsf) that is the destination of the created Admin Request note.

chAuthor  -  A pointer to the Author's name (hierarchical names MUST be in canonical format).

chSrcServer  -  A pointer to Source Server name (hierarchical names MUST be in canonical format).

chSrcPathName  -  A pointer to source file name including path relative to the Notes data directory.

chTitle  -  A pointer to the Title of the database being replicated (if the source database cannot be accessed to obtain the title, then this parameter should be NULL).

Replicainfo  -  Replicainfo - A pointer to source database Replicainfo (if the source database cannot be accessed by the caller then this parameter should be NULL).

chDesServer  -  A pointer to destination Server name (hierarchical names MUST be in canonical format).

chDesPathName  -  A pointer to destination file name including path relative to the Notes data directory.

arpAdminReqParamsPtr  -  Pointer to an ADMINReqParams structure.

wAdminReqParamsSize  -  Size of the buffer (ADMINReqParams structure) that the arpAdminReqParamsPtr parameter points to.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is.

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret code.



**Sample Usage :**
```
if (error = NSFDbReplicaInfoGet (hSrcDB, &replica_info))
{
	NSFDbClose (hSrcDB);
	return (ERR(error));
}

if (error = NSFDbOpen (AdminDBPath, &hAdminReq))
{
	NSFDbClose (hSrcDB);
	return (ERR(error));
 }

if (error = ADMINReqChkAccessNCMoveReplica (
	hAdminReq,
	"CN=Alan Admin/O=Org",
	SOURCE_SRVR,
	SOURCE_FILE,
	DB_TITLE,
	&replica_info,
	TARGET_SRVR,
	TARGET_FILE,
	&ARPptr,
	sizeof(ARPptr)) )
{
	NSFDbClose (hSrcDB);
	NSFDbClose (hAdminReq);
	return (ERR(error));
}
```
**See Also :**
[ADMINReqChkAccessMoveReplica](/reference/Func/ADMINReqChkAccessMoveReplica)
---
