




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



**ldap\_count\_messages** **- Get the
number of messages contained in a chain of results.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_count\_messages(**  

      LDAP \*ld,  

      LDAPMessage \*res**);**



**Description :**



This
function returns the number of messages contained in a chain of results.  This
can also be used to count the number of messages that remain in a chain if
called with a message returned by ldap\_first\_message or ldap\_next\_message.


 


Implemented
as a macro:


 


#define
ldap\_count\_messages(ld, res)         ND\_ldap\_count\_messages((ld), (res))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

res  -  The result chain, as obtained by a call to one of the synchronous
search routines or ldap\_result.  

  




Output :  

(routine)  -  mCount - The number of messages  contained in a chain of results.  

  

0 - No more messages.  

  

-1 - An error occured, such as the res parameter being invalid.  

  

  




 **Sample Usage :**


mCount =
ldap\_count\_messages(ld, res);


 **See Also :**


**[ldap\_first\_message](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/83517766FCD97E3385256F5C00488A80)**


**[ldap\_next\_message](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C2A0ABCC408C018A85256F5C00488A81)**



----------------------------------------------------------------------------------------------------------


 





