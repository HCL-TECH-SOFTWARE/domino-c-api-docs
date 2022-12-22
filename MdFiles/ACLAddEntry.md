




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



**ACLAddEntry** **- Adds an
entry to an access control list.**


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**



STATUS
LNPUBLIC **ACLAddEntry(**  

      DHANDLE  hACL,  

      const char far \*Name,  

      WORD  AccessLevel,  

      ACL\_PRIVILEGES far \*Privileges,  

      WORD  AccessFlags**);**



**Description :**



This
function adds an entry to an access control list.


 


**Parameters :**



Input :  

hACL  -  Handle to an access control list.  

  

Name  -  Null-terminated string pointer to user or group to be added.  If you
need to specify a hierarchical user name, be sure to use the fully
distinguished name.  

  

AccessLevel  -  Access level, ACL\_LEVEL\_xxx, of the entry to be added.  See
Symbolic Value, ACL\_LEVEL.  

  

Privileges  -  Pointer to privilege bit mask of the entry to be added.  Use
this parameter to assign roles to the entry.  See Data Type, ACL\_PRIVILEGES. 
See Data Type, ACL\_PRIVILEGES.  

  

AccessFlags  -  Access level modifier flags, ACL\_FLAG\_xxx  (eg:  unable to
delete documents, unable to create documents), of the entry to be added.  

  




Output :  

(routine)  -  Return status from this call - indicates either success
(NOERROR), or what the error is.  

  

  




 **See Also :**


**[ACL\_LEVEL\_xxx](ACL_LEVEL_xxx.md)**


**[ACL\_PRIVILEGES](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0007004A00E8002385255E3F00027E24)**


**[ACL\_FLAG\_xxx](ACL_FLAG_xxx.md)**


**[ACLCreate](ACLCreate.md)**


**[ACLDeleteEntry](ACLDeleteEntry.md)**



----------------------------------------------------------------------------------------------------------


 





