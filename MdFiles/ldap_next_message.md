




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



**ldap\_next\_message** **- Get the
next message in the list of messages.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



LDAPMessage
\* LNPUBLIC **ldap\_next\_message(**  

      LDAP \*ld,  

      LDAPMessage \*msg**);**



**Description :**



This
function gets the next message in the list of messages in a result chain
returned by ldap\_result.  For search operations, the result chain can actually
include referral messages, entry messages, and result messages.


 


Implemented
as a macro:


 


#define
ldap\_next\_message(ld, msg)           ND\_ldap\_next\_message((ld), (msg))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

msg  -  The message returned by a previous call to ldap\_first\_message or
ldap\_next\_message.  

  




Output :  

(routine)  -  Pointer to the next message of a message chain.  

  

NULL  - When no more messages exist in the result set to be returned or if an
error occurs while stepping through the entries, in which  

case the error parameters in the session handle ld will be set to indicate the
error.  

  

  




 **Sample Usage :**


nmsg =
ldap\_next\_message(ld, msg);


 **See Also :**


**[ldap\_count\_messages](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1F35BB007908496B85256F5C00488A82)**


**[ldap\_first\_message](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/83517766FCD97E3385256F5C00488A80)**



----------------------------------------------------------------------------------------------------------


 





