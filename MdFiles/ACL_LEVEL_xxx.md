




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



**ACL\_LEVEL\_xxx** **-** Access
Control Level symbols.


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**


 **Symbolic Values :**      ACL\_LEVEL\_NOACCESS     -  User or Server has no access to
the database.  

  

      ACL\_LEVEL\_DEPOSITOR    -  User or Server can add new data documents to a
database, but cannot examine the new document or the database.  

  

      ACL\_LEVEL\_READER          -  User or Server can only view data documents
in the database.  

  

      ACL\_LEVEL\_AUTHOR          -  User or Server can create and/or edit their
own data documents and examine existing ones in the database.  

  

      ACL\_LEVEL\_EDITOR           -  User or Server can create and/or edit any
data document.  

  

      ACL\_LEVEL\_DESIGNER      -  User or Server can create and/or edit any data
document and/or design document.  

  

      ACL\_LEVEL\_MANAGER       -  User or Server can create and/or maintain any
type of database or document, including the ACL.  

  

      ACL\_LEVEL\_HIGHEST         -  Highest access level.  

  

      ACL\_LEVEL\_COUNT            -  Number of access levels.  

  




**Description :**



Access
Control Level symbols used to qualify user or server access to a given Domino
database.


 **See Also :**


**[SECKFMUserInfo](SECKFMUserInfo.md)**


**[MAXUSERNAME](MAXUSERNAME.md)**


**[LICENSEID](LICENSEID.md)**


**[ACLLookupAccess](ACLLookupAccess.md)**


**[ACLAddEntry](ACLAddEntry.md)**


**[ACLUpdateEntry](ACLUpdateEntry.md)**


**[ACLEnumEntries](ACLEnumEntries.md)**



----------------------------------------------------------------------------------------------------------


 





