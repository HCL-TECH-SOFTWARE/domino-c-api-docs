##### Function : Administration Process
##### ADMINReqUpgradeToHier - Create an "Initiate Rename in Address Book" request.
---
##### #include <adminp.h>
STATUS LNPUBLIC **ADMINReqUpgradeToHier(**

	HCERTIFIER  hCertCtx,
	DBHANDLE  dbhNab,
	NOTEHANDLE  nhNote,
	char far *pOU,
	BOOL far *retfWeLoggedThisEntry,
	BOOL far *retfFatalError,
	ADMINReqParams far *arpAdminReqParamsPtr,
	WORD  wAdminReqParamsSize);
**Description :**
This function creates a "Initiate Rename in Address Book" request for a flat to 
hierarchical upgrade in the Administration Requests database (admin4.nsf).
**Parameters :**
Input :
hCertCtx  -  Handle to the current certifier context of the entity.

dbhNab  -  Handle to the Domino Directory (Server's Address book) .

nhNote  -  Handle to the note(person document) specifying the entity to be renamed.

pOU  -  new unique organization, if any, otherwise NULL

arpAdminReqParamsPtr  -  Pointer to an ADMINReqParams structure.

wAdminReqParamsSize  -  Size of the buffer (ADMINReqParams structure) that the arpAdminReqParamsPtr parameter points to.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is.  The return error codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret code.


retfWeLoggedThisEntry  -  TRUE if request has been recorded in the certification log.

retfFatalError  -  TRUE if an error occurred that would probably apply to many similar requests, e.g., can't even read the request DB.

**See Also :**
[ADMINReqDeleteInACL](D:/md_files/ADMINReqDeleteInACL.md)
[ADMINReqDeleteInNAB](D:/md_files/ADMINReqDeleteInNAB.md)
[ADMINReqMoveComplete](D:/md_files/ADMINReqMoveComplete.md)
[ADMINReqMoveUserInHier](D:/md_files/ADMINReqMoveUserInHier.md)
[ADMINReqParams](D:/md_files/ADMINReqParams.md)
[ADMINReqRecertify](D:/md_files/ADMINReqRecertify.md)
[ADMINReqRename](D:/md_files/ADMINReqRename.md)
---
