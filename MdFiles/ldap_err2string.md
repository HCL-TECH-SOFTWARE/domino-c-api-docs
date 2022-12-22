




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



**ldap\_err2string** **- Maps
numerical error codes to character strings.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



char
\*LNPUBLIC **ldap\_err2string(**  

      int  err**);**



**Description :**



This
function is used to convert a numeric LDAP result code, as returned by
ldap\_parse\_result or one of the synchronous API operation calls, into an
informative zero-terminated character string message describing the error.  


 


Implemented
as a macro:


 


#define
ldap\_err2string(err) ND\_ldap\_err2string((err)) 


 


**Parameters :**



Input :  

err  -  LDAP result code, as returned by ldap\_parse\_result or another LDAP API
call.  

  




Output :  

(routine)  -  A pointer to static data (it MUST NOT return NULL); the value
returned is always a valid null-terminated "C" string.  

  

  




 **See Also :**


**[ldap\_parse\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E8CA6F020C2423F385256F5C00488A71)**



----------------------------------------------------------------------------------------------------------


 





