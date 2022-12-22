




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



**ldap\_msgid** **- Return
the message ID associated with the LDAP message.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_msgid(**  

      LDAPMessage \*lm**);**



**Description :**



This
function returns the message ID associated with the LDAP message passed as a
parameter.


 


Implemented
as a macro:


 


#define
ldap\_msgid(lm)       ND\_ldap\_msgid((lm)) 


 


**Parameters :**



Input :  

lm  -  The result of an operation.    See ldap\_result.  

  




Output :  

(routine)  -  Message ID - Upon successful completion, returns the message ID
associated with an LDAP message.  

  

-1 - If an error occurs.  

  

  




 **Sample Usage :**


msgid = ldap\_msgid(lm);


 **See Also :**


**[ldap\_msgfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/ACE588BDB8F4BD8C85256F5C00488A70)**


**[ldap\_msgtype](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/24DD9BFD3ECF196785256F5C00488A74)**


**[ldap\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D5FCB8AF5BD5605D85256F5C00488A6F)**



----------------------------------------------------------------------------------------------------------


 





