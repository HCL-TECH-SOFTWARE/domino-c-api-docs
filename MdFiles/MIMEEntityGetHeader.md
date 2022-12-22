




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



**MIMEEntityGetHeader** **- get the
string value for the indicated header; returns a pointer to everything after
the field name, colon.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



const
char \* LNPUBLIC **MIMEEntityGetHeader(**  

      PMIMEENTITY  pMIMEEntity,  

      MIMESYMBOL  symKey**);**



**Description :**



This
function MIMEGetEntityHeader returns a pointer to the string value of the
header indicated by 'symKey'.  The string is everything after the header field
name and colon.  If the header is not found, MIMEGetEntityHeader returns NULL.


 


**Parameters :**



Input :  

pMIMEEntity  -  a pointer to current MIME entity.  

  

symKey  -   the MIMESYMBOL defined for the header.  

  




Output :  

(routine)  -  pointer to the header's string value.  

  

  




 **Sample Usage :**


HMIMEDIRECTORY
hMIMEDir;


STATUS error;


PMIMEENTITY
pRootEntity;


const char
\*pszHeaderValue;


 


if (error =
MIMEOpenDirectory(hNote, &hMIMEDir)) {


        goto exit;


}


 


if (error =
MIMEGetRootEntity(hNote, &pRootEntity)) {


        goto exit;


}


 


pszHeaderValue =
MIMEEntityGetHeader(pRootEntity, MIME\_SYMBOL\_CONTENT\_TYPE);


 


if (error =
MIMEFreeDirectory(hMIMEDir)) {


        goto exit;


}


 


 **See Also :**


**[MIMESYMBOL](MIMESYMBOL.md)**


**[PMIMEENTITY](PMIMEENTITY.md)**



----------------------------------------------------------------------------------------------------------


 





