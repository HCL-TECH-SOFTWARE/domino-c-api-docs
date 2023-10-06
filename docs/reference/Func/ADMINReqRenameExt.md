##### Function : Administration Process
##### ADMINReqRenameExt - Create a "Rename Person in Address Book" request.
---
```
#include <adminp.h>
STATUS LNPUBLIC ADMINReqRenameExt(

	HCERTIFIER  hCertCtx,
	DBHANDLE  dbhNab,
	NOTEHANDLE  nhNote,
	char far *pFirstName,
	char far *pMiddleInitial,
	char far *pLastName,
	char far *pOU,
	char far *pShortName,
	char far *pINetAddr,
	BOOL far *retfWeLoggedThisEntry,
	BOOL far *retfFatalError,
	ADMINReqParams far *arpAdminReqParamsPtr,
	WORD  wAdminReqParamsSize);
```
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

pOU  -  New unique organization, if any, otherwise NULL.

pShortName      -       new unique short name, if any, otherwise NULL.

pINetAddr     -                new unique internet address, if any, otherwise NULL.

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
       
if (error = ADMINReqRenameExt( 
 hCertCtx,
 hNABook,
 nhNote,
 "Joan",   /* New first name */
 "J",   /* New middle initial */
 "User",   /* New last name */
 NULL,
 "dadmin", /* New unique short name */
 "127.0.0.1", /* New unique internet address */
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
[ADMINReqRename](/domino-c-api-docs/reference/Func/ADMINReqRename)
[ADMINReqChkAccessNewReplica](/domino-c-api-docs/reference/Func/ADMINReqChkAccessNewReplica)
[ADMINReqDeleteInACL](/domino-c-api-docs/reference/Func/ADMINReqDeleteInACL)
[ADMINReqDeleteInNAB](/domino-c-api-docs/reference/Func/ADMINReqDeleteInNAB)
[ADMINReqMoveComplete](/domino-c-api-docs/reference/Func/ADMINReqMoveComplete)
[ADMINReqMoveUserInHier](/domino-c-api-docs/reference/Func/ADMINReqMoveUserInHier)
[ADMINReqParams](/domino-c-api-docs/reference/Data/ADMINReqParams)
[ADMINReqRecertify](/domino-c-api-docs/reference/Func/ADMINReqRecertify)
[ADMINReqUpgradeToHier](/domino-c-api-docs/reference/Func/ADMINReqUpgradeToHier)
---
