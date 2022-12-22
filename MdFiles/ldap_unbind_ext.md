




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



**ldap\_unbind\_ext** **- Close all
open connections associated with the LDAP session ID with client/server
controls.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_unbind\_ext(**  

      LDAP \*ld,  

      LDAPControl \*\*serverctrls,  

      LDAPControl \*\*clientctrls**);**



**Description :**



Utilizing 
client/server controls, this function closes all open connections associated
with the LDAP session ID, and disposes of all resources associated with the
session handle before returning.  


 


Note that
since there is no server response to an unbind request, there is no way to
receive a response to a server control sent with the unbind request. 


 


Implemented
as a macro:


 


#define
ldap\_unbind\_ext(ld, serverctrls, clientctrls)   ND\_ldap\_unbind\_ext((ld),
(serverctrls), (clientctrls))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server
controls are to be used.  

  

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client
controls are to be used.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  




 **See Also :**


**[ldap\_bind](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3844B80F7F75E54985256F5C00488A50)**


**[ldap\_bind\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3D3E64DE0C858A8D85256F5C00488A8B)**


**[LDAP\_OPT\_xxx](LDAP_OPT_xxx.md)**


**[ldap\_sasl\_bind](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A41092FC030B4C1B85256F5C00488A51)**


**[ldap\_sasl\_bind\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/77A8C62045FB561785256F5C00488A9E)**


**[ldap\_simple\_bind](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/843F0C387CD49FA885256F5C00488A89)**


**[ldap\_simple\_bind\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/83B177C9401D75A585256F5C00488A8A)**


**[ldap\_unbind](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7B1B0198A981BDA285256F5C00488A78)**


**[ldap\_unbind\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E48665257460FDBE85256F5C00488A8C)**



----------------------------------------------------------------------------------------------------------


 





