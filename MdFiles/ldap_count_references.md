




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



**ldap\_count\_references** **- Get the
number of references contained in a chain of results.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_count\_references(**  

      LDAP \*ld,  

      LDAPMessage \*chain**);**



**Description :**



This
function returns the number of references contained in a chain of results. 
This can also be used to count the number of references that remain in a chain
if called with a reference returned by ldap\_first\_reference or
ldap\_next\_reference.


 


Implemented
as a macro:


 


#define
ldap\_count\_references(ld, chain)     ND\_ldap\_count\_references((ld), (chain))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

chain  -  The result chain, as obtained by a call to one of the synchronous
search routines or ldap\_result.  

  




Output :  

(routine)  -  rCount - The number of references  contained in a chain of
results.  

  

0 - No more references.  

  

-1 - An error occured, such as the chain parameter being invalid.  

  

  




 **Sample Usage :**


rCount =
ldap\_count\_references(Id, chain);


 **See Also :**


**[ldap\_first\_reference](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/01E57F4C687A7B8285256F5C00488A84)**


**[ldap\_next\_message](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C2A0ABCC408C018A85256F5C00488A81)**


**[ldap\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D5FCB8AF5BD5605D85256F5C00488A6F)**



----------------------------------------------------------------------------------------------------------


 





