




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



**Function : LDAP**



**ldap\_abandon** **- Perform
an LDAP abandon operation.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_abandon(**  

      LDAP \*ld,  

      int  msgid**);**



**Description :**



This
function will perform an LDAP abandon of an operation in progress.


 


Implemented
as a macro:


 


#define
ldap\_abandon(ld, msgid)     ND\_ldap\_abandon((ld), (msgid))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

msgid  -  Message ID of the request to be abandoned.  

  




Output :  

(routine)  -  0 on success and -1 on error.  

  

  




 




----------------------------------------------------------------------------------------------------------


 





