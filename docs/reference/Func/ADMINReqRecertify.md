##### Function : Administration Process
##### ADMINReqRecertify - Create a "Recertify Person in Address Book" request. 
---
```
#include <adminp.h>
STATUS LNPUBLIC ADMINReqRecertify(

	HCERTIFIER  hCertCtx,
	DBHANDLE  dbhNab,
	NOTEHANDLE  nhNote,
	BOOL far *retfWeLoggedThisEntry,
	BOOL far *retfFatalError,
	ADMINReqParams far *arpAdminReqParamsPtr,
	WORD  wAdminReqParamsSize);
```
**Description :**

This function creates a "Recertify Person in Address Book" request in the 
Administration Requests database (admin4.nsf).

**Parameters :**
Input :
hCertCtx  -  Handle to the current certifier context of the entity.

dbhNab  -  Handle to the Domino Directory (Server's Address book) .

nhNote  -  Handle to the note (person document) specifying the entity to be recertified.

arpAdminReqParamsPtr  -  Pointer to an ADMINReqParams structure.

wAdminReqParamsSize  -  Size of the buffer (ADMINReqParams structure) that the arpAdminReqParamsPtr parameter points to.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is.  The return error codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret code.


retfWeLoggedThisEntry  -  Currently not used. You still need to allocate memory for this return parameter.  Future releases of Notes/Domino will return TRUE if request has been recorded in the certification log.

retfFatalError  -  Currently not used. You still need to allocate memory for this return parameter.  Future releases of Notes/Domino will return TRUE if an error occurred that may apply to many similar requests, e.g., can't even read the request DB.


**Sample Usage :**
```
if (error = NSFDbOpen (FullDBPath, &hNABook))
{
 return (ERR(error));
}

if (error = REGFindAddressBookEntry (hNABook, 
 "$Users", 
 DNAME,
 &NoteID))
{
 NSFDbClose (hNABook);
 return (ERR(error));
}

if (error = NSFNoteOpen(hNABook, NoteID, 0, &nhNote))
{
 NSFDbClose (hNABook);
 return (ERR(error));
}

if (error = GetCertCtx(CERT_ID, &hCertCtx, "password"))
{
 NSFNoteClose (nhNote);
 NSFDbClose (hNABook);
 return (ERR(error));
}
      
if (error = ADMINReqRecertify (
 hCertCtx,
 hNABook,
 nhNote,
 &logged,
 &ferror,
 &ARPptr,
 sizeof(ARPptr)) )
{
 SECKFMFreeCertifierCtx (hCertCtx);
 NSFNoteClose (nhNote);
 NSFDbClose (hNABook);
 return (ERR(error));
}
```
**See Also :**
[ADMINReqChkAccessMoveReplica](/domino-c-api-docs/reference/Func/ADMINReqChkAccessMoveReplica)
[ADMINReqChkAccessNewReplica](/domino-c-api-docs/reference/Func/ADMINReqChkAccessNewReplica)
[ADMINReqDeleteInACL](/domino-c-api-docs/reference/Func/ADMINReqDeleteInACL)
[ADMINReqDeleteInNAB](/domino-c-api-docs/reference/Func/ADMINReqDeleteInNAB)
[ADMINReqMoveComplete](/domino-c-api-docs/reference/Func/ADMINReqMoveComplete)
[ADMINReqMoveUserInHier](/domino-c-api-docs/reference/Func/ADMINReqMoveUserInHier)
[ADMINReqParams](/domino-c-api-docs/reference/Data/ADMINReqParams)
[ADMINReqRename](/domino-c-api-docs/reference/Func/ADMINReqRename)
[ADMINReqUpgradeToHier](/domino-c-api-docs/reference/Func/ADMINReqUpgradeToHier)
---
