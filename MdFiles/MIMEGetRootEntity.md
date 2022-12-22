




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 7.0.2**



**Function : MIME**



**MIMEGetRootEntity** **- Get the
root entity of the MIME directory; i.e., the first part in the MIME message.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEGetRootEntity(**  

      HMIMEDIRECTORY  hMIMEDir,  

      PMIMEENTITY \*retpMIMEEntity**);**



**Description :**



This
function MIMEGetRootEntity returns a pointer to the root entity of an open
MIMEDIRECTORY.  The "root entity" is the first part in the MIME
message from which the directory was constructed.  The root entity pointer can
be used in other MIME API calls to traverse the directory or to get specific
information about the root entity; e.g., the MIME content type.


 


 


**Parameters :**



Input :  

hMIMEDir  -  a handle to an open MIMEDIRECTORY.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully accessed the MIMEDIRECTORY.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

retpMIMEEntity  -  a pointer to the directory's root entity.  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pMIMEEntity;


BOOL bIsMultiPart =
FALSE;


BOOL bIsMessagePart =
FALSE;


BOOL bIsDiscretePart =
FALSE;


 


if (error =
MIMEOpenDirectory(hNote, &hMIMEDir)) {


        goto exit;


}


 


if (error =
MIMEGetRootEntity(hNote, &pMIMEEntity)) {


        goto exit;


}


 


if
(MIMEEntityIsMultiPart(pMIMEEntity)) {


        bIsMultiPart =
TRUE;


}


else if
(MIMEEntityIsMessagePart(pMIMEEntity)) {


        bIsMessagePart
= TRUE;


}


else if
(MIMEEntityIsDiscretePart(pMIMEEntity)) {


        bIsDiscretePart
= TRUE;


}


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto e


 


 **See Also :**


**[HMIMEDIRECTORY](HMIMEDIRECTORY.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





