




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



**ldap\_first\_reference** **- Get the
first reference in the list of references.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



LDAPMessage
\* LNPUBLIC **ldap\_first\_reference(**  

      LDAP \*ld,  

      LDAPMessage \*chain**);**



**Description :**



This
function gets the first reference in the list of references in a result chain
returned by ldap\_result.  For search operations, the result chain can actually
include referral messages, entry messages, and result messages.


 


Implemented
as a macro:


 


#define
ldap\_first\_reference(ld, chain)          ND\_ldap\_first\_reference((ld), (chain))



 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

chain  -  The result chain, as obtained by a call to one of the synchronous
search routines or ldap\_result.  

  




Output :  

(routine)  -  Pointer to the first reference in a chain of references.  

  

NULL  - When no more references exist in the result set to be returned or if an
error occurs while stepping through the entries, in which  

case the error parameters in the session handle ld will be set to indicate the
error.  

  

  




 **Sample Usage :**


ref =
ldap\_first\_reference(ld, chain);


 **See Also :**


**[ldap\_count\_references](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/22F1A3A8362CB7B685256F5C00488A86)**


**[ldap\_next\_reference](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/744AB45C6395CFE785256F5C00488A85)**


**[ldap\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D5FCB8AF5BD5605D85256F5C00488A6F)**



----------------------------------------------------------------------------------------------------------


 





