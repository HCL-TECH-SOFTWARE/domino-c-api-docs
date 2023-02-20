##### Function : Administration Process
##### ADMINReqMoveUserInHier - Create a "Move Person in Hierarchy" request. 
---
```
#include <adminp.h>
STATUS LNPUBLIC ADMINReqMoveUserInHier(

	HCERTIFIER  hCertCtx,
	DBHANDLE  dbhNab,
	NOTEHANDLE  nhNote,
	char far *pTargetCert,
	BOOL far *retfWeLoggedThisEntry,
	BOOL far *retfFatalError,
	ADMINReqParams far *arpAdminReqParamsPtr,
	WORD  wAdminReqParamsSize);
```
**Description :**

This function creates a "Move Person in Hierarchy" request in the 
Administration Requests database (admin4.nsf).

**Parameters :**
Input :
hCertCtx  -  Handle to the current certifier context of the entity.

dbhNab  -  Handle to the Domino Directory (Server's Address book) .

nhNote  -  Handle to the note (person document) specifying the entity to be recertified.

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

if (error = NSFNoteOpen (hNABook, NoteID, 0, &nhNote))
{
 NSFDbClose (hNABook);
 return (ERR(error));
}

if (error = GetCertCtx (CERT_ID, &hCertCtx, "password"))
{
 NSFNoteClose (nhNote);
 NSFDbClose (hNABook);
 return (ERR(error));
}
      
if (error = ADMINReqMoveUserInHier (
 hCertCtx,
 hNABook,
 nhNote,
 "O=ABCorp/C=US", /* Target Certifier */
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
[ADMINReqChkAccessMoveReplica](/reference/Func/ADMINReqChkAccessMoveReplica)
[ADMINReqChkAccessNewReplica](/reference/Func/ADMINReqChkAccessNewReplica)
[ADMINReqDeleteInACL](/reference/Func/ADMINReqDeleteInACL)
[ADMINReqDeleteInNAB](/reference/Func/ADMINReqDeleteInNAB)
[ADMINReqMoveComplete](/reference/Func/ADMINReqMoveComplete)
[ADMINReqParams](/reference/Data/ADMINReqParams)
[ADMINReqRecertify](/reference/Func/ADMINReqRecertify)
[ADMINReqRename](/reference/Func/ADMINReqRename)
[ADMINReqUpgradeToHier](/reference/Func/ADMINReqUpgradeToHier)
---
