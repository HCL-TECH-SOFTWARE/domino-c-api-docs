




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



**ACL\_UPDATE\_xxx** **-** ACLUpdateEntry
flags.


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**


 **Symbolic Values :**      ACL\_UPDATE\_NAME           -  The user's name is to be
modified. The user entry is deleted and a new entry is created. Unless the
other access control information is specified to be modified as well, the other
access control information will be cleared and the user will have No Access to
the database.  

  

      ACL\_UPDATE\_LEVEL          -  The user's access level is to be modified.  

  

      ACL\_UPDATE\_PRIVILEGES             -  The user's assigned privileges or
roles are to be modified.  

  

      ACL\_UPDATE\_FLAGS          -  The user's access level modifier (eg: unable
to delete documents) is to be modified.  

  




**Description :**



Use these
symbols when calling ACLUpdateEntry to specify what to modify in the access
control list.  These values may be bitwise-OR'd together to modify multiple
parameters.


 **See Also :**


**[ACLLookupAccess](ACLLookupAccess.md)**


**[ACLAddEntry](ACLAddEntry.md)**


**[ACLUpdateEntry](ACLUpdateEntry.md)**


**[ACLEnumEntries](ACLEnumEntries.md)**



----------------------------------------------------------------------------------------------------------


 





