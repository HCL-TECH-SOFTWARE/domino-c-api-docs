




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



**ldap\_msgtype** **- Returns
the type of the LDAP message.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_msgtype(**  

      LDAPMessage \*lm**);**



**Description :**



This
function returns the type of the LDAP message it is passed as a parameter.  It
can be used to distinguish between the different message types: referral
messages, entry messages, and result\_messages.  See LDAP\_RES\_xxx.


 


Implemented
as a macro:


 


#define
ldap\_msgtype(lm)   ND\_ldap\_msgtype((lm))


 


**Parameters :**



Input :  

lm  -  The result(s) of an operation.    See ldap\_result.  

  




Output :  

(routine)  -  LDAP\_RES\_xxx - Upon successful completion, returns the LDAP
message type.  

  

-1 - If an error occurs.  

  

  




 **See Also :**


**[ldap\_first\_entry](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0238B4B4403930DA85256F5C00488A5F)**


**[ldap\_first\_message](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/83517766FCD97E3385256F5C00488A80)**


**[ldap\_first\_reference](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/01E57F4C687A7B8285256F5C00488A84)**


**[ldap\_msgfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/ACE588BDB8F4BD8C85256F5C00488A70)**


**[ldap\_msgid](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E912825DE531A38285256F5C00488A75)**


**[ldap\_next\_entry](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/838CF92EE872121885256F5C00488A60)**


**[ldap\_next\_message](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C2A0ABCC408C018A85256F5C00488A81)**


**[ldap\_next\_reference](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/744AB45C6395CFE785256F5C00488A85)**


**[ldap\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D5FCB8AF5BD5605D85256F5C00488A6F)**



----------------------------------------------------------------------------------------------------------


 





