




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Access Control List**



**ACLSetPriv** **- Sets the
given bit in an ACL\_PRIVILEGES structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**



void **ACLSetPriv(**  

      ACL\_PRIVILEGES  Priv,  

      WORD  Num**);**



**Description :**



This is a
macro that sets the given bit in an ACL\_PRIVILEGES structure.


 


**Parameters :**



Input :  

Priv  -  Privilege bit mask.  The privilege bit mask is a structure where each
bit represents a role that may be set for each entry in an access control
list.  The first five bits (bit number 0 through 4) are reserved for the five
"privilege levels", used in versions of Notes before Release 3.  
Each of the other bits maps to a role name.  Roles are assigned to an access
control list entry by setting the appropriate bits in the privilege bit mask.  

  

Num  -  The bit number (0 through ACL\_PRIVCOUNT - 1) of the bit to be set.  

  




Output :  

(routine)  -  none  

  

  

Priv  -  The resulting privilege bit mask with the desired bit set.  

  




 **See Also :**


**[ACLClearPriv](ACLClearPriv.md)**


**[ACL\_PRIVILEGES](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0007004A00E8002385255E3F00027E24)**


**[ACLInvertPriv](ACLInvertPriv.md)**


**[ACLIsPrivSet](ACLIsPrivSet.md)**



----------------------------------------------------------------------------------------------------------


 





