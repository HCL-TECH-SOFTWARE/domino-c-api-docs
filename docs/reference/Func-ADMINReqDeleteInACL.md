##### Function : Administration Process
##### ADMINReqDeleteInACL - Create a "Delete in Access Control List" request.
---
##### #include <adminp.h>
STATUS LNPUBLIC **ADMINReqDeleteInACL(**

	DBHANDLE  dbhAdmin4,
	char far *chAuthor,
	char far *chUserName,
	char far *chMailServerName,
	char far *chMailFileName,
	char far *chDeleteMailFile,
	ADMINReqParams far *arpAdminReqParamsPtr,
	WORD  wAdminReqParamsSize);
**Description :**
This function creates a "Delete in Access Control List" request in the 
Administration Requests database (admin4.nsf).

(NOTE: Although this function creates a "Delete in Access Control List" request 
in the Administration Requests database, the calling application is responsible 
to remove the Person document from the Domino Directory (Server's Address book) 
being administered.  This behavior will be addressed in a future release of 
Domino.)
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

if (error = ADMINReqDeleteInACL (
 hAdminReq,
 "CN=Alan Admin/O=Org",
 "CN=Joe User/O=Org",
 MAIL_SRVR,
 MAIL_FILE,
 "1",
 &ARPptr,
 sizeof(ARPptr)) )
{
 error = NSFDbClose (hAdminReq);
 return (ERR(error));
}
```
**See Also :**
[ADMINReqChkAccessMoveReplica](D:/md_files/ADMINReqChkAccessMoveReplica.md)
[ADMINReqChkAccessNewReplica](D:/md_files/ADMINReqChkAccessNewReplica.md)
[ADMINReqDeleteInNAB](D:/md_files/ADMINReqDeleteInNAB.md)
[ADMINReqMoveComplete](D:/md_files/ADMINReqMoveComplete.md)
[ADMINReqMoveUserInHier](D:/md_files/ADMINReqMoveUserInHier.md)
[ADMINReqParams](D:/md_files/ADMINReqParams.md)
[ADMINReqRecertify](D:/md_files/ADMINReqRecertify.md)
[ADMINReqRename](D:/md_files/ADMINReqRename.md)
---
