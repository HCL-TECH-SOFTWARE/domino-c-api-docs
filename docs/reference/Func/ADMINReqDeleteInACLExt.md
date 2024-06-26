##### Function : Administration Process
##### ADMINReqDeleteInACLExt - Create a "Delete in Access Control List" request.
---
```
#include <adminp.h>
STATUS LNPUBLIC ADMINReqDeleteInACLExt(

	DBHANDLE  dbhAdmin4,
	char far *chAuthor,
	char far *chUserName,
	char far *chMailServerName,
	char far *chMailFileName,
	char far *chDeleteMailFile,
	char far *chIDVaultFlag,
	char far *chIDVaultName,
	ADMINReqParams far *arpAdminReqParamsPtr,
	WORD  wAdminReqParamsSize);
```

**Description :**

This function creates a &quot;Delete in Access Control List&quot; request in the Administration Requests database (admin4.nsf).
<ul><br>
<br>
(NOTE: Although this function creates a &quot;Delete in Access Control List&quot; request in the Administration Requests database, the calling application is responsible to remove the Person document from the Domino Directory (Server's Address book) being administered.  This behavior will be addressed in a future release of Domino.)</ul>



**Parameters :**
Input :
dbhAdmin4  -  Handle of the Administration Request database (admin4.nsf) that is the destination of the created Admin Request note.

chAuthor  -  A pointer to the Author's name (hierarchical names MUST be in canonical format).

chUserName  -  A pointer to the User's name being deleted (hierarchical names MUST be in canonical format).

chMailServerName  -  A pointer to the Mail Server name (hierarchical names MUST be in canonical format).

chMailFileName  -  A pointer to the Mail file name including path relative to the Domino data directory.

chDeleteMailFile  -  A pointer to a string indicating whether to delete the mail file:

          "0" = Don't delete mail file
          "1" = Delete just mail file specified in person record
          "2" = Delete mail file specified in person record & all replicas

chIDVaultFlag  -  A pointer to string indicating whether or not to delete the user from the ID vault or mark them inactive.
 "0" = Don't delete, just mark as inactive
"1" = Delete the user from the vault
"2" = Don't do anything with the user's ID in the vault

chIDVaultName  -  A pointer to string indicating which vault the user is in.

wAdminReqParamsSize  -  Size of the buffer (ADMINReqParams structure) that the arpAdminReqParamsPtr parameter points to.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is.

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret code.


arpAdminReqParamsPtr  -  Pointer to an ADMINReqParams structure.



**Sample Usage :**
```
if (error = NSFDbOpen (AdminDBPath, &hAdminReq))
{
	return (ERR(error));
}

if (error = ADMINReqDeleteInACLExt (
 hAdminReq,
 "CN=Alan Admin/O=Org",
 "CN=Joe User/O=Org",
 MAIL_SRVR,
 MAIL_FILE,
 "1",
 "1",
 "testVault",
 &ARPptr,
 sizeof(ARPptr)) )
{
 error = NSFDbClose (hAdminReq);
 return (ERR(error));
}
```

**See Also :**
[ADMINReqChkAccessMoveReplica](/domino-c-api-docs/reference/Func/ADMINReqChkAccessMoveReplica)
[ADMINReqChkAccessNewReplica](/domino-c-api-docs/reference/Func/ADMINReqChkAccessNewReplica)
[ADMINReqDeleteInNAB](/domino-c-api-docs/reference/Func/ADMINReqDeleteInNAB)
[ADMINReqMoveComplete](/domino-c-api-docs/reference/Func/ADMINReqMoveComplete)
[ADMINReqMoveUserInHier](/domino-c-api-docs/reference/Func/ADMINReqMoveUserInHier)
[ADMINReqParams](/domino-c-api-docs/reference/Data/ADMINReqParams)
[ADMINReqRecertify](/domino-c-api-docs/reference/Func/ADMINReqRecertify)
[ADMINReqRename](/domino-c-api-docs/reference/Func/ADMINReqRename)
---
