




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



**MIMEEntityIsMessagePart** **- test
input MIME entity to determine if it is a 'message' content type with child
entities.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



BOOL
LNPUBLIC **MIMEEntityIsMessagePart(**  

      PMIMEENTITY  pMIMEEntity**);**



**Description :**



This
function MIMEEntityIsMessagePart returns TRUE if the input MIME entity is a
message/rfc822 MIME entity and has child entities.


 


 


**Parameters :**



Input :  

pMIMEEntity  -  a pointer to current MIME entity.  

  




Output :  

(routine)  -  TRUE if input MIME entity is a message/rfc822 entity with child
entities, otherwise FALSE.  

  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


BOOL bIsMessagePart =
FALSE;


 


if (error =
MIMEOpenDirectory(hNote, &hMIMEDir)) {


        goto exit;


}


 


if (error =
MIMEGetRootEntity(hNote, &pRootEntity)) {


        goto exit;


}


 


bIsMessagePart =
MIMEEntityIsMessagePart(pRootEntity);


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


}


 


 **See Also :**


**[MIMEEntityIsDiscretePart](MIMEEntityIsDiscretePart.md)**


**[MIMEEntityIsMultiPart](MIMEEntityIsMultiPart.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





