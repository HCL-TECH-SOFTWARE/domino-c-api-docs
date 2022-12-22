




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



**ADMINReqMoveComplete** **- Create an
"Initiate Rename in Address Book" request.**


**----------------------------------------------------------------------------------------------------------**



**#include <adminp.h>**



STATUS
LNPUBLIC **ADMINReqMoveComplete(**  

      HCERTIFIER  hCertCtx,  

      DBHANDLE  dbhAdmin4,  

      NOTEHANDLE  nhAdminReq,  

      char far \*pTargetCert,  

      BOOL far \*retfWeLoggedThisEntry,  

      BOOL far \*retfFatalError,  

      ADMINReqParams far \*arpAdminReqParamsPtr,  

      WORD  wAdminReqParamsSize**);**



**Description :**



This
function creates a "Initiate Rename in Address Book" request in the
Administration Requests database (admin4.nsf). This function is intended to be
used on the server only.


 


**Parameters :**



Input :  

hCertCtx  -  Handle to the current certifier context of the entity.  

  

dbhAdmin4  -  Handle to admin4 request database.  

  

nhAdminReq  -  Handle to AdminpMoveUserInHier note in admin4 request database.  

  

pTargetCert  -  The name of New certifier name canonical format (e.g.:
"O=ABCorp/C=US").  

  

arpAdminReqParamsPtr  -  Pointer to an ADMINReqParams structure.  

  

wAdminReqParamsSize  -  Size of the buffer (ADMINReqParams structure) that the
arpAdminReqParamsPtr parameter points to.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is.  The return error codes include:  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret code.  

  

  

retfWeLoggedThisEntry  -  Currently not used. You still need to allocate memory
for this return parameter.  Future releases of Domino will return TRUE if an
error occurred that may apply to many similar requests, e.g., can't even read
the request DB.  

  

retfFatalError  -  Currently not used. You still need to allocate memory for
this return parameter.  Future releases of Domino will return TRUE if an error
occurred that may apply to many similar requests, e.g., can't even read the
request DB.  

  




 **Sample Usage :**



if (error =
NSFDbOpen (AdminDBPath, &hAdminReq))


{


            return
(ERR(error));


}


 


/\*
Obtain NoteID of admin request via whatever method preferred \*/ 


 


if
(error = NSFNoteOpen (hAdminReq, NoteID, 0, &nhAdminReq))


{


            NSFDbClose
(hAdminReq);


            return
(ERR(error));


}


 


if
(error = GetCertCtx (CERT\_ID, &hCertCtx, "password"))


{


            NSFNoteClose
(nhAdminReq);


            NSFDbClose
(hAdminReq);


            return
(ERR(error));


}


     



if
(error = ADMINReqMoveComplete (


            hCertCtx,


            hAdminReq,


            nhAdminReq,


            "O=ABCorp/C=US",
/\* Target Certifier \*/


            &logged,


            &ferror,


            &ARPptr,


            sizeof(ARPptr))
)


{


            SECKFMFreeCertifierCtx
(hCertCtx);


            NSFNoteClose
(nhAdminReq);


            NSFDbClose
(hAdminReq);


            return
(ERR(error));


}


 **See Also :**


**[ADMINReqChkAccessMoveReplica](ADMINReqChkAccessMoveReplica.md)**


**[ADMINReqChkAccessNewReplica](ADMINReqChkAccessNewReplica.md)**


**[ADMINReqDeleteInACL](ADMINReqDeleteInACL.md)**


**[ADMINReqDeleteInNAB](ADMINReqDeleteInNAB.md)**


**[ADMINReqMoveUserInHier](ADMINReqMoveUserInHier.md)**


**[ADMINReqParams](ADMINReqParams.md)**


**[ADMINReqRecertify](ADMINReqRecertify.md)**


**[ADMINReqRename](ADMINReqRename.md)**


**[ADMINReqUpgradeToHier](ADMINReqUpgradeToHier.md)**



----------------------------------------------------------------------------------------------------------


 





