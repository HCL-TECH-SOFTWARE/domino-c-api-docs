




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



**ldap\_count\_entries** **- Get the
number of entries contained in a chain of results.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_count\_entries(**  

      LDAP \*ld,  

      LDAPMessage \*chain**);**



**Description :**



This
function returns the number of entries contained in a chain of results.  This
can also be used to count the number of entries that remain in a chain if
called with an entry, or reference returned by ldap\_first\_entry or
ldap\_next\_entry.


 


Implemented
as a macro:


 


#define ldap\_count\_entries(ld,
chain)           ND\_ldap\_count\_entries((ld), (chain))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

chain  -  The result chain, as obtained by a call to one of the synchronous
search routines or ldap\_result.  

  




Output :  

(routine)  -  The number of entries  contained in a chain of results.  

  

0 - No more entries.  

  

-1 - An error occured, such as the chain parameter being invalid.  

  

  




 **Sample Usage :**


eCount =
ldap\_count\_entries(Id, chain);


 **See Also :**


**[ldap\_first\_entry](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0238B4B4403930DA85256F5C00488A5F)**


**[ldap\_next\_entry](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/838CF92EE872121885256F5C00488A60)**


**[ldap\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D5FCB8AF5BD5605D85256F5C00488A6F)**



----------------------------------------------------------------------------------------------------------


 





