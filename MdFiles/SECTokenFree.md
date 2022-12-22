




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



**Function : User Registration**



**SECTokenFree** **- Free a
Single Sign-On Token.**


**----------------------------------------------------------------------------------------------------------**



**#include <bsafe.h>**



void
LNPUBLIC **SECTokenFree(**  

      MEMHANDLE \*mhToken**);**



**Description :**



Use this
function to free the memory associated with an SSO\_TOKEN structure. There is no
need to unlock the structure or its members before freeing, this call will
unlock all outstanding locks.


 


**Parameters :**



Input :  

mhToken  -  Pointer to a MEMHANDLE returned from a call to SECTokenGenerate.  

  




Output :  

(routine)  -  None.  

  

  




 **See Also :**


**[SECTokenGenerate](SECTokenGenerate.md)**


**[SECTokenValidate](SECTokenValidate.md)**


**[SSO\_TOKEN](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/ABE1F48EEAFAA02E85256BC10067CE9E)**



----------------------------------------------------------------------------------------------------------


 





