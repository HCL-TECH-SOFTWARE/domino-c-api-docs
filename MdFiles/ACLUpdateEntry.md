




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



**ACLUpdateEntry** **- Updates
an entry in an access control list.**


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**



STATUS
LNPUBLIC **ACLUpdateEntry(**  

      DHANDLE  hACL,  

      const char far \*Name,  

      WORD  UpdateFlags,  

      const char far \*NewName,  

      WORD  NewAccessLevel,  

      ACL\_PRIVILEGES far \*NewPrivileges,  

      WORD  NewAccessFlags**);**



**Description :**



This
function updates an entry in an access control list.    

  

Unless the user's name is specified to be modified, the information that is not
specified to be modified remains intact.  If the user's name is specified to be
modified, the user entry is deleted and a new entry is created.  Unless the
other access control information is specified to be modified as well, the other
access control information will be cleared and the user will have No Access to
the database.


 


**Parameters :**



Input :  

hACL  -  Handle to an access control list.  

  

Name  -  Null-terminated string pointer to user or group to be updated.  Use
NULL to update the default name.  If you need to specify a hierarchical user
name, be sure to use the fully distinguished name.  

  

UpdateFlags  -   Update flags, ACL\_UPDATE\_xxx, specifying which fields to
update.  These flags may be OR'd together to update multiple fields.  

  

NewName  -  Null-terminated string pointer to new user or group name.  Ignored
if UpdateFlags does not indicate that the name is to be updated.  Otherwise,
the user entry is deleted and a new entry is created.  Unless the other access
control information is specified to be modified as well, the other access
control information will be cleared and the user will have No Access to the
database.  

  

NewAccessLevel  -  New access level, ACL\_LEVEL\_xxx.  Ignored if UpdateFlags
does not indicate that the access level is to be updated.  

  

NewPrivileges  -  Pointer to new privileges bit mask.  See Data Type,
ACL\_PRIVILEGES.  Ignored  if UpdateFlags does not indicate that the privileges
are to be updated.   

  

NewAccessFlags  -   New access level modifier flags, ACL\_FLAG\_xxx  (eg:  unable
to delete documents, unable to create documents).  Ignored if UpdateFlags does
not indicate that the access level modifier flags are to be updated.  

  




Output :  

(routine)  -  Return status from this call - indicates either success
(NOERROR), or what the error is.  

  

  




 **See Also :**


**[ACL\_UPDATE\_xxx](ACL_UPDATE_xxx.md)**


**[ACL\_PRIVILEGES](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0007004A00E8002385255E3F00027E24)**


**[ACL\_LEVEL\_xxx](ACL_LEVEL_xxx.md)**


**[ACL\_FLAG\_xxx](ACL_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





