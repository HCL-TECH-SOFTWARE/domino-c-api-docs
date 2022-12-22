




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



**MIMEGetFirstSubpart** **- Get the
first child of the current multipart entity.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEGetFirstSubpart(**  

      HMIMEDIRECTORY  hMIMEDir,  

      PMIMEENTITY  pMIMEEntity,  

      PMIMEENTITY \*retpMIMEEntity**);**



**Description :**



This
function MIMEGetFirstSubpart returns a pointer to the input entity's first
child entity, if the input entity is a composite entity; i.e., a multipart
entity.  If the current entity is not a multipart entity or if it contains no
child entities, then MIMEGetFirstSubpart returns a NULL pointer in the output
argument, retpMIMEEntity.


 


**Parameters :**



Input :  

hMIMEDir  -  a handle to an open MIMEDIRECTORY.  

  

pMIMEEntity  -  a pointer to a MIME entity.  This should be a multipart entity.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully accessed the directory.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

retpMIMEEntity  -  a pointer to the input entity's first child entity.  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


PMIMEENTITY pChildEntity;  

MIMESYMBOL  msContentType;


 


if (error =
MIMEOpenDirectory(hNote, &hMIMEDir)) {


        goto exit;


}


 


if (error =
MIMEGetRootEntity(hNote, &pRootEntity)) {


        goto exit;


}


 


if
(MIMEEntityIsMultiPart(pRootEntity)) {


        if (error =
MIMEGetFirstSubpart(hMIMEDir, pRootEntity, &pChildEntity)) {


               goto
exit;


        }


 


        msContentType =
MIMEEntityContentType(pChildEntity);


}


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


}


 


 **See Also :**


**[HMIMEDIRECTORY](HMIMEDIRECTORY.md)**


**[MIMEGetNextSibling](MIMEGetNextSibling.md)**


**[MIMEGetParent](MIMEGetParent.md)**


**[MIMEGetPrevSibling](MIMEGetPrevSibling.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





