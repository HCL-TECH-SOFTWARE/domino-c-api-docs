




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Data Type : Access Control List**



**ACL\_PRIVILEGES** **-** Privilege
bit array.


**----------------------------------------------------------------------------------------------------------**



**#include
<acl.h>**



**Definition :**



typedef struct {BYTE
BitMask[10]} ACL\_PRIVILEGES;


 


**Description :**



This
structure is the privilege bit mask which is an array of bytes (totaling
ACL\_PRIVCOUNT number of bits).  Each bit represents a role.  The first five
bits (bit number 0 through 4) are reserved for the five "privilege
levels", used in versions of Notes before Release 3.  Each of the other
bits maps to a role name.  Roles are assigned to an access control list entry
by setting the appropriate bits in the prviliege bit mask.


 **See Also :**


**[ACLAddEntry](ACLAddEntry.md)**


**[ACLClearPriv](ACLClearPriv.md)**


**[ACLEnumEntries](ACLEnumEntries.md)**


**[ACLGetPrivName](ACLGetPrivName.md)**


**[ACLInvertPriv](ACLInvertPriv.md)**


**[ACLIsPrivSet](ACLIsPrivSet.md)**


**[ACLLookupAccess](ACLLookupAccess.md)**


**[ACLSetPriv](ACLSetPriv.md)**


**[ACLSetPrivName](ACLSetPrivName.md)**


**[ACLUpdateEntry](ACLUpdateEntry.md)**


**[ACL\_BITPRIVxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2E89AC8E96CCAEA3852561E0006F1580)**


**[ACL\_PRIVCOUNT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5E96D013CF3AC495852561E0006F157D)**



----------------------------------------------------------------------------------------------------------


 





