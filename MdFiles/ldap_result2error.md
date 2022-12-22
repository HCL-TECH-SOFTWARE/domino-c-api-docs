




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



**ldap\_result2error** **- Return an
error code from an LDAP result message.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_result2error(**  

      LDAP \*ld,  

      LDAPMessage \*r,  

      int  freeit**);**



**Description :**



This
function returns an error code from an LDAP result message.


 


Implemented
as a macro:


 


#define
ldap\_result2error(ld, r, freeit)                        ND\_ldap\_result2error((ld),
(r), (freeit)) 


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

r  -  The result of an LDAP operation as returned by ldap\_result or one of the
synchronous API operation calls.  

  

freeit  -  A boolean that determines whether the result parameter is  disposed
of or not.  If freeit is non-zero, the entire chain of messages represented by
result is disposed of after extracting the requested information. This is
provided as a convenience; zero can also be passed, to not free the messages,
and ldap\_msgfree can be used to free the result later.  

  




Output :  

(routine)  -  LDAP error code.  

  

  




 **Sample Usage :**


err = ldap\_result2error(Id, r, 1);


 **See Also :**


**[ldap\_err2string](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/EE09788FC00F5AB985256F5C00488A56)**



----------------------------------------------------------------------------------------------------------


 





