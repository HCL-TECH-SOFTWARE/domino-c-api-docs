




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



**MIMEEntityContentSubtype** **- return
the content subtype for the input MIME entity.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



MIMESYMBOL
LNPUBLIC **MIMEEntityContentSubtype(**  

      PMIMEENTITY  pMIMEEntity**);**



**Description :**



This
function MIMEEntityContentSubtype returns the content subtype of the input MIME
Entity; i.e., a MIMESYMBOL.


 


**Parameters :**



Input :  

pMIMEEntity  -  a pointer to a MIME entity.  

  




Output :  

(routine)  -  the MIMESYMBOL for the entity's content subtype.  

  

  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pMIMEEntity;


BOOL bIsAlternative =
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
(MIMEEntityContentType(pMIMEEntity) == MIME\_SYMBOL\_MULTIPART


&& 
MIMEEntityContentSubtype(pMIMEEntity) == MIME\_SYMBOL\_ALTERNATIVE) {


        bIsAlternative
= TRUE;


}


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


}


 


 **See Also :**


**[MIMEEntityContentType](MIMEEntityContentType.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





