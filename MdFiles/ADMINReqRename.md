




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 4.6.2**



**Function : Administration Process**



**ADMINReqRename** **- Create a
"Rename Person in Address Book" request.**


**----------------------------------------------------------------------------------------------------------**



**#include <adminp.h>**



STATUS
LNPUBLIC **ADMINReqRename(**  

      HCERTIFIER  hCertCtx,  

      DBHANDLE  dbhNab,  

      NOTEHANDLE  nhNote,  

      char far \*pFirstName,  

      char far \*pMiddleInitial,  

      char far \*pLastName,  

      char far \*pOU,  

      BOOL far \*retfWeLoggedThisEntry,  

      BOOL far \*retfFatalError,  

      ADMINReqParams far \*arpAdminReqParamsPtr,  

      WORD  wAdminReqParamsSize**);**



**Description :**



This
function creates a "Rename Person in Address Book" request the
Administration Requests database (admin4.nsf).


 


**Parameters :**



Input :  

hCertCtx  -  Handle to the current certifier context of the entity.  

  

dbhNab  -  Handle to the Domino Directory (Server's Address book) .  

  

nhNote  -  Handle to the note(person document) specifying the entity to be
renamed.  

  

pFirstName  -  New first name (MUST be NULL if it's not a person entry).  

  

pMiddleInitial  -  New middle initial (MUST be NULL if it's not a person
entry).  

  

pLastName  -  New last name.  

  

pOU  -  New unique organization, if any, otherwise NULL  

  

arpAdminReqParamsPtr  -  Pointer to an ADMINReqParams structure.  

  

wAdminReqParamsSize  -  Size of the buffer (ADMINReqParams structure) that the
arpAdminReqParamsPtr parameter points to.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is.  The return error codes include:  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret code.  

  

  

retfWeLoggedThisEntry  -  TRUE if request has been recorded in the
certification log.  

  

retfFatalError  -  TRUE if an error occurred that would probably apply to many
similar requests, e.g., can't even read the request DB.  

  




 **Sample Usage :**


if (error =
NSFDbOpen (FullDBPath, &hNABook))  

{  

      return (ERR(error));  

}


 


if (error =
REGFindAddressBookEntry (hNABook,   

      "$Users",   

       DNAME,  

      &NoteID))  

{  

      NSFDbClose (hNABook);  

      return (ERR(error));  

}


 


if (error =
NSFNoteOpen(hNABook, NoteID, 0, &nhNote))  

{  

      NSFDbClose (hNABook);  

      return (ERR(error));  

}


 


if (error =
GetCertCtx(CERT\_ID, &hCertCtx, "password"))  

{  

      NSFDbClose (hNABook);  

      return (ERR(error));  

}  

         

if (error = ADMINReqRename(   

      hCertCtx,  

      hNABook,  

      nhNote,  

      "Joan",   /\* New first name \*/  

      "J",         /\* New middle initial \*/  

      "User",   /\* New last name \*/  

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


 **See Also :**


**[ADMINReqChkAccessMoveReplica](ADMINReqChkAccessMoveReplica.md)**


**[ADMINReqChkAccessNewReplica](ADMINReqChkAccessNewReplica.md)**


**[ADMINReqDeleteInACL](ADMINReqDeleteInACL.md)**


**[ADMINReqDeleteInNAB](ADMINReqDeleteInNAB.md)**


**[ADMINReqMoveComplete](ADMINReqMoveComplete.md)**


**[ADMINReqMoveUserInHier](ADMINReqMoveUserInHier.md)**


**[ADMINReqParams](ADMINReqParams.md)**


**[ADMINReqRecertify](ADMINReqRecertify.md)**


**[ADMINReqUpgradeToHier](ADMINReqUpgradeToHier.md)**



----------------------------------------------------------------------------------------------------------


 





