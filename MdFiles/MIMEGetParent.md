




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



**MIMEGetParent** **- get a
pointer to the parent MIME entity for the input MIME entity.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEGetParent(**  

      HMIMEDIRECTORY  hMIMEDir,  

      PMIMEENTITY  pMIMEEntity,  

      PMIMEENTITY \*retpMIMEEntity**);**



**Description :**



This
function MIMEGetParent returns a pointer to the parent MIME entity for the
input MIME entity.  If the input MIME entity has no parent --i.e., it is the
root MIME entity for the MIME directory-- MIMEGetParent returns a NULL pointer
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

  

  

  

retpMIMEEntity  -  a pointer to the parent entity.  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


PMIMEENTITY
pCurrEntity;


PMIMEENTITY
pHTMLParentEntity;


 


if (error =
MIMEOpenDirectory(hNote, &hMIMEDir)) {


        goto exit;


}


 


if (error =
MIMEGetRootEntity(hNote, &pRootEntity)) {


        goto exit;


}


 


pCurrEntity =
pRootEntity;


 


while (pCurrEntity) {


        if
(MIMEEntityContentType(pChildEntity) == MIME\_SYMBOL\_HTML) {


               if
(error = MIMEGetParent(hMIMEDir, pChildEntity, &pHTMLParentEntity)) {


                       goto
exit


               }


               break;


        }


        if (error =
MIMEIterateNext(hMIMEDir, pRootEntity, pCurrEntity, &pCurrEntity)) {


               goto
exit;


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


**[MIMEGetPrevSibling](MIMEGetPrevSibling.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





