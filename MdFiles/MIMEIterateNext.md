




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



**MIMEIterateNext** **- Get the
next MIME entity in the MIME directory**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEIterateNext(**  

      HMIMEDIRECTORY  hMIMEDir,  

      PMIMEENTITY  pTopMIMEEntity,  

      PMIMEENTITY  pPrevMIMEEntity,  

      PMIMEENTITY \*retpMIMEEntity**);**



**Description :**



This
function MIMEIterateNext returns a pointer to the next entity in an open
MIMEDIRECTORY.  Note that MIMEIterateNext traverses the MIME directory in depth
first order so that it visits the MIME entities in the order in which they
appear in the original MIME message.


 


 


**Parameters :**



Input :  

hMIMEDir  -  a handle to an open MIMEDIRECTORY.  

  

pTopMIMEEntity  -  a pointer to topmost MIME entity for this traversal;
typically the root entity.  

  

pPrevMIMEEntity  -  a pointer to the previously visited MIME entity; usually
the initial value for this is the root entity pointer.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully accessed the MIMEDIRECTORY.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

retpMIMEEntity  -  a pointer to the previously visited MIME entity; usually the
initial value for this is the root entity pointer.  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


PMIMEENTITY
pCurrEntity;


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
MIMEGetRootEntity(hNote, &pRootEntity)) {


        goto exit;


}


 


pCurrEntity =
pRootEntity;


do {


        if
(MIMEEntityIsMultiPart(pCurrEntity)) {


               bIsMultiPart
= TRUE;


        }


        else if
(MIMEEntityIsMessagePart(pCurrEntity)) {


               bIsMessagePart
= TRUE;


        }


        else if
(MIMEEntityIsDiscretePart(pCurrEntity)) {


               bIsDiscretePart
= TRUE;


        }


 


        error =
MIMEIterateNext(hMIMEDir, pRootEntity, pCurrEntity, &pCurrEntity);


} while (error ==
NOERROR && pCurrEntity != NULL);


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


}


 


 **See Also :**


**[HMIMEDIRECTORY](HMIMEDIRECTORY.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





