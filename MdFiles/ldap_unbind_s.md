




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




**Initial Release 6**



**Function : LDAP**



**ldap\_unbind\_s** **- Close all
open connections associated with the LDAP session ID.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_unbind\_s(**  

      LDAP \*ld**);**



**Description :**



This
function closes all open connections associated with the LDAP session ID, and
disposes of all resources associated with the session handle before returning.


 


Implemented
as a macro:


 


#define
ldap\_unbind\_s(ld)    ND\_ldap\_unbind\_s((ld)) 


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  




Output :  

(routine)  -   LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  




 **Sample Usage :**



ldap\_unbind\_s(
ld );


 **See Also :**


**[ldap\_bind\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3D3E64DE0C858A8D85256F5C00488A8B)**


**[ldap\_sasl\_bind\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/77A8C62045FB561785256F5C00488A9E)**


**[ldap\_simple\_bind\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/83B177C9401D75A585256F5C00488A8A)**


**[ldap\_unbind](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7B1B0198A981BDA285256F5C00488A78)**


**[ldap\_unbind\_ext](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E2E050F5C129555085256F5C00488A79)**



----------------------------------------------------------------------------------------------------------


 





