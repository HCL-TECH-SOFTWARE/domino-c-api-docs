




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



**ldap\_get\_entry\_controls** **- Extract
LDAP controls from an entry.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_get\_entry\_controls(**  

      LDAP \*ld,  

      LDAPMessage \*entry,  

      LDAPControl \*\*\*ctrls**);**



**Description :**



This
function is is used to extract LDAP controls from an entry.


 


Implemented
as a macro:


 


#define
ldap\_get\_entry\_controls(ld, entry, ctrls)        ND\_ldap\_get\_entry\_controls((ld),
(entry), (ctrls))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

entry  -  The entry to extract controls from, as returned by ldap\_first\_entry
or ldap\_next\_entry.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the controls are successfully returned, or
another LDAP result code if the value of the controls are undefined.  

  

  

ctrls  -  An allocated array of controls copied out of the entry. The control
array  SHOULD be freed by calling ldap\_controls\_free.  NULL, if no controls
were returned.  

  




 **See Also :**


**[ldap\_control\_free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5712ED91000A9CE285256F5C00488A7B)**


**[ldap\_first\_entry](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0238B4B4403930DA85256F5C00488A5F)**


**[ldap\_next\_entry](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/838CF92EE872121885256F5C00488A60)**



----------------------------------------------------------------------------------------------------------


 





