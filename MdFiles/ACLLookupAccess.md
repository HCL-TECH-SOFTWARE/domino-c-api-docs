




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



**ACLLookupAccess** **- Returns
ACL information for the specified names.**


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**



STATUS
LNPUBLIC **ACLLookupAccess(**  

      DHANDLE  hACL,  

      NAMES\_LIST far \*pNamesList,  

      WORD far \*retAccessLevel,  

      ACL\_PRIVILEGES far \*retPrivileges,  

      WORD far \*retAccessFlags,  

      DHANDLE far \*rethPrivNames**);**



**Description :**



This
function looks up all the specified names in the access control list and
returns the maximum of the authorized level and privileges.  If none of the
specified names are found in the list, the level and privileges for the default
entry are returned.  If no names are supplied, then the level and privileges
for the minimal entry are returned.  

  

If the ACL contains multiple occurrences of a name, this function applies the same
rules as the Notes User Interface when determining which access level takes
precedence.  For example, if a user's name is included in the ACL, and that
name is also a member of a group included in the ACL, then the explicit name
will always take precedence--even if it has a lower access level than the group
name.


 


**Parameters :**



Input :  

hACL  -  Handle to an access control list.  

  

pNamesList  -   Pointer to a NAMES\_LIST structure.  The user name and then all
group names that the user is a member of (directly or indirectly) must
immediately follow the NAMES\_LIST structure as contiguous null-terminated LMBCS
strings.  If this pointer is NULL, then the access information of the entry
with the minimum access is returned.  If the pointer is not NULL, then the NAMES\_LIST
must have at least a user name in it.  Otherwise, the default access is
returned.  If you need to specify a hierarchical user name, be sure to use the
fully distinguished name.  

  




Output :  

(routine)  -  Return status from this call - indicates either success
(NOERROR), or what the error is.  

  

  

retAccessLevel  -   Pointer to the returned access level, ACL\_LEVEL\_xxx.  See
Symbolic Value, ACL\_LEVEL.  

  

retPrivileges  -  Pointer to returned privilege bit mask.  See Data Type,
ACL\_PRIVILEGES.  

  

retAccessFlags  -  Pointer to returned access level modifier flags,
ACL\_FLAG\_xxx  (eg:  unable to delete documents, unable to create documents).  

  

rethPrivNames  -  Pointer to a handle to a text list which contains the
privilege names or roles for that user.  Use OSLockObject to obtain a pointer
to this text list.  ListGetText may then be used to get the entries in this
text list.  After processing the text list, use OSUnlockObject to unlock the
text list pointer and OSMemFree to free the memory associated with this handle.  

  




 **See Also :**


**[ACL\_LEVEL\_xxx](ACL_LEVEL_xxx.md)**


**[ACL\_PRIVILEGES](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0007004A00E8002385255E3F00027E24)**


**[ACL\_FLAG\_xxx](ACL_FLAG_xxx.md)**


**[NAMES\_LIST](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/009F0044002000E285255E3F0001744B)**



----------------------------------------------------------------------------------------------------------


 





