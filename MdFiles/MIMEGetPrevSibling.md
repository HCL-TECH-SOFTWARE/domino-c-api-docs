




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



**MIMEGetPrevSibling** **- Get the
previous MIME entity at the current 'level'; e.g., the previous alternative
within a multipart/alternative.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEGetPrevSibling(**  

      HMIMEDIRECTORY  hMIMEDir,  

      PMIMEENTITY  pMIMEEntity,  

      PMIMEENTITY \*retpMIMEEntity**);**



**Description :**



This
function MIMEGetPrevSibling returns a pointer to the previous sibling entity;
i.e., the previous child entity of some parent multipart entity.  If there are
no siblings or no previous siblings, MIMEPrevNextSibling returns a NULL pointer
in the retpMIMEEntity output argument.


 


 


**Parameters :**



Input :  

hMIMEDir  -  a handle to an open MIMEDIRECTORY.  

  

pMIMEEntity  -  a pointer to current MIME entity.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully accessed the MIMEDIRECTORY.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

retpMIMEEntity  -  a pointer to the previous sibling entity.  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


PMIMEENTITY
pChildEntity;


PMIMEENTITY
pEntityBeforeHTML;


 


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
MIMEGetFirstSubPart(hMIMEDir, pRootEntity, &pChildEntity)) {


               goto
exit;


        }


 


        while
(pChildEntity) {


               if
(MIMEEntityContentType(pChildEntity) == MIME\_SYMBOL\_HTML) {


                       if
(error = MIMEGetPrevSibling(hMIMEDir, pChildEntity, &pEntityBeforeHTML)) {


                              goto
exit


                       }


                       break;


               }


 


               if
(error = MIMEGetNextSibling(hMIMEDir, pChildEntity, &pChildEntity)) {


                       goto
exit;


               }


        }


}


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


}


 


 **See Also :**


**[HMIMEDIRECTORY](HMIMEDIRECTORY.md)**


**[MIMEGetFirstSubpart](MIMEGetFirstSubpart.md)**


**[MIMEGetNextSibling](MIMEGetNextSibling.md)**


**[MIMEGetParent](MIMEGetParent.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





