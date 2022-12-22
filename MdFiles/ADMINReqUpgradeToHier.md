




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




**Initial Release 6**



**Function : Administration Process**



**ADMINReqUpgradeToHier** **- Create an
"Initiate Rename in Address Book" request.**


**----------------------------------------------------------------------------------------------------------**



**#include <adminp.h>**



STATUS
LNPUBLIC **ADMINReqUpgradeToHier(**  

      HCERTIFIER  hCertCtx,  

      DBHANDLE  dbhNab,  

      NOTEHANDLE  nhNote,  

      char far \*pOU,  

      BOOL far \*retfWeLoggedThisEntry,  

      BOOL far \*retfFatalError,  

      ADMINReqParams far \*arpAdminReqParamsPtr,  

      WORD  wAdminReqParamsSize**);**



**Description :**



This
function creates a "Initiate Rename in Address Book" request for a
flat to hierarchical upgrade in the Administration Requests database
(admin4.nsf).


 


**Parameters :**



Input :  

hCertCtx  -  Handle to the current certifier context of the entity.  

  

dbhNab  -  Handle to the Domino Directory (Server's Address book) .  

  

nhNote  -  Handle to the note(person document) specifying the entity to be
renamed.  

  

pOU  -  new unique organization, if any, otherwise NULL  

  

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

  




 **See Also :**


**[ADMINReqDeleteInACL](ADMINReqDeleteInACL.md)**


**[ADMINReqDeleteInNAB](ADMINReqDeleteInNAB.md)**


**[ADMINReqMoveComplete](ADMINReqMoveComplete.md)**


**[ADMINReqMoveUserInHier](ADMINReqMoveUserInHier.md)**


**[ADMINReqParams](ADMINReqParams.md)**


**[ADMINReqRecertify](ADMINReqRecertify.md)**


**[ADMINReqRename](ADMINReqRename.md)**



----------------------------------------------------------------------------------------------------------


 





