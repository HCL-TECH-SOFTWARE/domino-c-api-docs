




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



**ldap\_msgfree** **- Free each
message in the result chain.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_msgfree(**  

      LDAPMessage \*lm**);**



**Description :**



This
function frees each message in the result chain and returns the type of the
last message in the chain.  If result is NULL, nothing is done and the value
zero is returned.  See LDAP\_RES\_xxx.


 


Implemented
as a macro:


 


#define
ldap\_msgfree(lm)    ND\_ldap\_msgfree((lm))             


 


**Parameters :**



Input :  

lm  -  The result(s) of an operation.  See ldap\_result.  

  




Output :  

(routine)  -  LDAP\_RES\_xxx - Upon successful completion, returns the LDAP
message type.  

  

0 - Result is NULL.  

  

-1 - If an error occurs.  

  

  




 **See Also :**


**[ldap\_msgid](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E912825DE531A38285256F5C00488A75)**


**[ldap\_msgtype](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/24DD9BFD3ECF196785256F5C00488A74)**


**[ldap\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D5FCB8AF5BD5605D85256F5C00488A6F)**


**[LDAP\_RES\_xxx](LDAP_RES_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





