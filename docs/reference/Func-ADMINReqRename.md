##### Function : Administration Process
##### ADMINReqRename - Create a "Rename Person in Address Book" request.
---
##### #include <adminp.h>
STATUS LNPUBLIC **ADMINReqRename(**

	HCERTIFIER  hCertCtx,
	DBHANDLE  dbhNab,
	NOTEHANDLE  nhNote,
	char far *pFirstName,
	char far *pMiddleInitial,
	char far *pLastName,
	char far *pOU,
	BOOL far *retfWeLoggedThisEntry,
	BOOL far *retfFatalError,
	ADMINReqParams far *arpAdminReqParamsPtr,
	WORD  wAdminReqParamsSize);
**Description :**
This function creates a "Rename Person in Address Book" request the 
Administration Requests database (admin4.nsf).
**Parameters :**
Input :
hCertCtx  -  Handle to the current certifier context of the entity.

dbhNab  -  Handle to the Domino Directory (Server's Address book) .

nhNote  -  Handle to the note(person document) specifying the entity to be renamed.

pFirstName  -  New first name (MUST be NULL if it's not a person entry).

pMiddleInitial  -  New middle initial (MUST be NULL if it's not a person entry).

pLastName  -  New last name.

pOU  -  New unique organization, if any, otherwise NULL

arpAdminReqParamsPtr  -  Pointer to an ADMINReqParams structure.

wAdminReqParamsSize  -  Size of the buffer (ADMINReqParams structure) that the arpAdminReqParamsPtr parameter points to.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is.  The return error codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret code.


retfWeLoggedThisEntry  -  TRUE if request has been recorded in the certification log.

retfFatalError  -  TRUE if an error occurred that would probably apply to many similar requests, e.g., can't even read the request DB.

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
 NSFDbClose (hNABook);
 return (ERR(error));
}
       
if (error = ADMINReqRename( 
 hCertCtx,
 hNABook,
 nhNote,
 "Joan",   /* New first name */
 "J",   /* New middle initial */
 "User",   /* New last name */
 NULL,
 &logged,
 &ferror,
 &ARPptr,
 sizeof(ARPptr)) )
{
 SECKFMFreeCertifierCtx (hCertCtx);
 NSFDbClose (hNABook);
 return (ERR(error));
}
```
**See Also :**
[ADMINReqChkAccessMoveReplica](D:/md_files/ADMINReqChkAccessMoveReplica.md)
[ADMINReqChkAccessNewReplica](D:/md_files/ADMINReqChkAccessNewReplica.md)
[ADMINReqDeleteInACL](D:/md_files/ADMINReqDeleteInACL.md)
[ADMINReqDeleteInNAB](D:/md_files/ADMINReqDeleteInNAB.md)
[ADMINReqMoveComplete](D:/md_files/ADMINReqMoveComplete.md)
[ADMINReqMoveUserInHier](D:/md_files/ADMINReqMoveUserInHier.md)
[ADMINReqParams](D:/md_files/ADMINReqParams.md)
[ADMINReqRecertify](D:/md_files/ADMINReqRecertify.md)
[ADMINReqUpgradeToHier](D:/md_files/ADMINReqUpgradeToHier.md)
---
