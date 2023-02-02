##### Function : Administration Process
##### ADMINReqMoveComplete - Create an "Initiate Rename in Address Book" request.
---
##### #include <adminp.h>
STATUS LNPUBLIC **ADMINReqMoveComplete(**

	HCERTIFIER  hCertCtx,
	DBHANDLE  dbhAdmin4,
	NOTEHANDLE  nhAdminReq,
	char far *pTargetCert,
	BOOL far *retfWeLoggedThisEntry,
	BOOL far *retfFatalError,
	ADMINReqParams far *arpAdminReqParamsPtr,
	WORD  wAdminReqParamsSize);
**Description :**
This function creates a "Initiate Rename in Address Book" request in the 
Administration Requests database (admin4.nsf). This function is intended to be 
used on the server only.
**Parameters :**
Input :
hCertCtx  -  Handle to the current certifier context of the entity.

dbhAdmin4  -  Handle to admin4 request database.

nhAdminReq  -  Handle to AdminpMoveUserInHier note in admin4 request database.

pTargetCert  -  The name of New certifier name canonical format (e.g.: "O=ABCorp/C=US").

arpAdminReqParamsPtr  -  Pointer to an ADMINReqParams structure.

wAdminReqParamsSize  -  Size of the buffer (ADMINReqParams structure) that the arpAdminReqParamsPtr parameter points to.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is.  The return error codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret code.


retfWeLoggedThisEntry  -  Currently not used. You still need to allocate memory for this return parameter.  Future releases of Domino will return TRUE if an error occurred that may apply to many similar requests, e.g., can't even read the request DB.

retfFatalError  -  Currently not used. You still need to allocate memory for this return parameter.  Future releases of Domino will return TRUE if an error occurred that may apply to many similar requests, e.g., can't even read the request DB.

**Sample Usage :**
```
if (error = NSFDbOpen (AdminDBPath, &hAdminReq))
{
	return (ERR(error));
}

/* Obtain NoteID of admin request via whatever method preferred */ 

if (error = NSFNoteOpen (hAdminReq, NoteID, 0, &nhAdminReq))
{
	NSFDbClose (hAdminReq);
	return (ERR(error));
}

if (error = GetCertCtx (CERT_ID, &hCertCtx, "password"))
{
	NSFNoteClose (nhAdminReq);
	NSFDbClose (hAdminReq);
	return (ERR(error));
}
      
if (error = ADMINReqMoveComplete (
	hCertCtx,
	hAdminReq,
	nhAdminReq,
	"O=ABCorp/C=US", /* Target Certifier */
	&logged,
	&ferror,
	&ARPptr,
	sizeof(ARPptr)) )
{
	SECKFMFreeCertifierCtx (hCertCtx);
	NSFNoteClose (nhAdminReq);
	NSFDbClose (hAdminReq);
	return (ERR(error));
}
```
**See Also :**
[ADMINReqChkAccessMoveReplica](D:/md_files/ADMINReqChkAccessMoveReplica.md)
[ADMINReqChkAccessNewReplica](D:/md_files/ADMINReqChkAccessNewReplica.md)
[ADMINReqDeleteInACL](D:/md_files/ADMINReqDeleteInACL.md)
[ADMINReqDeleteInNAB](D:/md_files/ADMINReqDeleteInNAB.md)
[ADMINReqMoveUserInHier](D:/md_files/ADMINReqMoveUserInHier.md)
[ADMINReqParams](D:/md_files/ADMINReqParams.md)
[ADMINReqRecertify](D:/md_files/ADMINReqRecertify.md)
[ADMINReqRename](D:/md_files/ADMINReqRename.md)
[ADMINReqUpgradeToHier](D:/md_files/ADMINReqUpgradeToHier.md)
---
