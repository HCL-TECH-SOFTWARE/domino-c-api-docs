




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



**ACL\_FLAG\_xxx** **-** Access level
modifier flags.


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**


 **Symbolic Values :**      ACL\_FLAG\_AUTHOR\_NOCREATE   -  User has access level of
author and cannot create new notes (can only edit existing ones).  

  

      ACL\_FLAG\_SERVER            -  Entry represents a Server  

  

      ACL\_FLAG\_NODELETE       -  User cannot delete notes.  

  

      ACL\_FLAG\_CREATE\_PRAGENT      -  User can create personal agents  

  

      ACL\_FLAG\_CREATE\_PRFOLDER    -  User can create personal folders  

  

      ACL\_FLAG\_PERSON           -  Entry represents a Person  

  

      ACL\_FLAG\_GROUP             -  Entry represents a group  

  

      ACL\_FLAG\_CREATE\_FOLDER         -  User can create and update shared views
& folders. This allows an Editor to assume some Designer-level access  

  

      ACL\_FLAG\_CREATE\_LOTUSSCRIPT          -  User can create LotusScript  

  

      ACL\_FLAG\_PUBLICREADER            -  User can read public notes  

  

      ACL\_FLAG\_PUBLICWRITER            -  User can write public notes  

  

      ACL\_FLAG\_ADMIN\_SERVER           -  Entry is administration server  

  

      ACL\_FLAG\_MONITORS\_DISALLOWED        -  User cannot register headline
monitors for this database.  

  

      ACL\_FLAG\_NOREPLICATE              -  User cannot replicate or copy this
database.  

  




**Description :**



These
symbols represent access level modifier flags in access control lists.  Each
access level taken by itself implies a certain set of immutable capabilities.
Each access level has a different set of access modifier bits that are relevant
for that level.  All of the other bits that are returned in the Access Flag
parameter of C API functions are irrelevant and are unpredictable. The table
below depicts which Access Level Modifier Flags (ACL\_FLAG\_xxx) are applicable
to the Access Levels (ACL\_LEVEL\_xxx).


 


 




|  |  |
| --- | --- |
| **ACL\_LEVEL\_xxx** | **ACL\_FLAG\_xxx Applicable** 
**to ACL\_LEVEL\_xxx** |
| ACL\_LEVEL\_MANAGER | ACL\_FLAG\_NODELETE
ACL\_FLAG\_PERSON
ACL\_FLAG\_GROUP
ACL\_FLAG\_SERVER |
| ACL\_LEVEL\_DESIGNER | ACL\_FLAG\_NODELETE
ACL\_FLAG\_CREATE\_LOTUSSCRIPT
ACL\_FLAG\_PERSON
ACL\_FLAG\_GROUP
ACL\_FLAG\_SERVER |
| ACL\_LEVEL\_EDITOR | ACL\_FLAG\_NODELETE
ACL\_FLAG\_CREATE\_PRAGENT
ACL\_FLAG\_CREATE\_PRFOLDER
ACL\_FLAG\_CREATE\_FOLDER
ACL\_FLAG\_CREATE\_LOTUSSCRIPT
ACL\_FLAG\_PERSON
ACL\_FLAG\_GROUP
ACL\_FLAG\_SERVER |
| ACL\_LEVEL\_AUTHOR | ACL\_FLAG\_AUTHOR\_NOCREATE
ACL\_FLAG\_NODELETE
ACL\_FLAG\_CREATE\_PRAGENT
ACL\_FLAG\_CREATE\_PRFOLDER
ACL\_FLAG\_CREATE\_LOTUSSCRIPT
ACL\_FLAG\_PUBLICWRITER
ACL\_FLAG\_PERSON
ACL\_FLAG\_GROUP
ACL\_FLAG\_SERVER |
| ACL\_LEVEL\_READER | ACL\_FLAG\_CREATE\_PRAGENT
ACL\_FLAG\_CREATE\_PRFOLDER
ACL\_FLAG\_CREATE\_LOTUSSCRIPT
ACL\_FLAG\_PUBLICWRITER
ACL\_FLAG\_PERSON
ACL\_FLAG\_GROUP
ACL\_FLAG\_SERVER |
| ACL\_LEVEL\_DEPOSITOR | ACL\_FLAG\_PUBLICREADER
ACL\_FLAG\_PUBLICWRITER
ACL\_FLAG\_PERSON
ACL\_FLAG\_GROUP
ACL\_FLAG\_SERVER |
| ACL\_LEVEL\_NOACCESS | ACL\_FLAG\_PUBLICREADER
ACL\_FLAG\_PUBLICWRITER
ACL\_FLAG\_PERSON
ACL\_FLAG\_GROUP
ACL\_FLAG\_SERVER |


 


 **See Also :**


**[ACLLookupAccess](ACLLookupAccess.md)**


**[ACLAddEntry](ACLAddEntry.md)**


**[ACLUpdateEntry](ACLUpdateEntry.md)**


**[ACLEnumEntries](ACLEnumEntries.md)**


**[NSFDbAccessGet](NSFDbAccessGet.md)**



----------------------------------------------------------------------------------------------------------


 





