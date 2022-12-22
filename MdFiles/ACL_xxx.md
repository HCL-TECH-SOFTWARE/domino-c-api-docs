




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




**Initial Release 4.0**



**Symbolic Value : Access Control List**



**ACL\_xxx** **-** ACL-wide
flags.  Get and set with ACLGetFlags and ACLSetFlags.


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**


 **Symbolic Values :**      ACL\_UNIFORM\_ACCESS     -  Require same ACL in ALL replicas
of database  

  

      ACL\_FLAG\_ADMIN\_READERAUTHOR         -  Admin server can modify reader and
author fields in database  

  




**Description :**



These flags
apply to the access control list itself.


 **See Also :**


**[ACLGetFlags](ACLGetFlags.md)**


**[ACLSetFlags](ACLSetFlags.md)**



----------------------------------------------------------------------------------------------------------


 





