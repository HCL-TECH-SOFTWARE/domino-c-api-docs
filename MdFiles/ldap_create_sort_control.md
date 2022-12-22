




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



**ldap\_create\_sort\_control** **- Create
and encode the server-side sort control.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_create\_sort\_control(**  

      LDAP \*ld,  

      LDAPsortKey \*\*keyList,  

      char  isCritical,  

      LDAPControl \*\*ctrlp**);**



**Description :**



This
function will  create and encode the server-side sort control.


 


Implemented
as a macro:


 


#define
ldap\_create\_sort\_control(ld, keyList, isCritical, ctrlp)\


             
ND\_ldap\_create\_sort\_control((ld), (keyList), (isCritical), (ctrlp))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

keyList  -  Pointer to a NULL terminated array of pointers to LDAPsortKey
structures.  

  

isCritical  -  Zero indicates the control is not critical to the operation, and
non-zero indicates the control is critical to the operation.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the sort control was successfully created, or
another LDAP result code if not.  

  

  

ctrlp  -  Returns a pointer to the LDAPControl created.  This control SHOULD be
freed by calling ldap\_control\_free when done.  

  




 **See Also :**


**[ldap\_control\_free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5712ED91000A9CE285256F5C00488A7B)**



----------------------------------------------------------------------------------------------------------


 





