




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




 


**Symbolic Value : Access Control List**



**ACL\_SUBGROUP\_xxx** **-** Privilege
name delimiters.


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**


 **Symbolic Values :**      ACL\_SUBGROUP\_LEFT\_PAREN      -  '[' - Opening delimiter for
role names.  

  

      ACL\_SUBGROUP\_RIGHT\_PAREN   -  ']' - Closing delimiter for role names.  

  




**Description :**



Beginning
with Release 3 of Notes, up to 75 named "roles" may be defined for
access control lists.  A role is added to an access control list by setting the
appropriate privilege bit in the ACL\_PRIVILEGES structure.  Role names begin
with a left square bracket and end with a right square bracket.


 **See Also :**


**[ACLGetPrivName](ACLGetPrivName.md)**


**[ACLSetPrivName](ACLSetPrivName.md)**


**[ACL\_PRIVILEGES](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0007004A00E8002385255E3F00027E24)**



----------------------------------------------------------------------------------------------------------


 





