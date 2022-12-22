




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



**ACLEnumEntries** **-
Enumerates an access control list's entries.**


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**



STATUS
LNPUBLIC **ACLEnumEntries(**  

      DHANDLE  hACL,  

      void LNCALLBACKPTR  EnumFunc,  

      void far \*EnumFuncParam**);**



**Description :**



This function
enumerates the entries in an access control list.


 


**Parameters :**



Input :  

hACL  -   Handle to an access control list.  

  

EnumFunc  -  Far pointer to a user defined EnumFunc callback function.  This
callback function is called with information about each entry in the list and
is defined as:  

  

      void (LNCALLBACKPTR EnumFunc)(  

                              void far \*EnumFuncParam,  

                              char far \*Name,  

                              WORD AccessLevel,  

                              ACL\_PRIVILEGES far \*Privileges,  

                              WORD AccessFlags)  

  

The EnumFuncParam argument is a pointer to data that has been passed to
ACLEnumEntries to be used by EnumFunc.  The Name argument is the user name. 
The AccessLevel argument is the access level (ACL\_LEVEL\_xxx).  The Privileges
argument is a pointer to the privilege bit mask (see the Data Type,
ACL\_PRIVILEGES).  The AccessFlags argument is the access level modifier flags
(ACL\_FLAG\_xxx).  

  

The callback function cannot be used to modify the access control list.  

  

EnumFuncParam  -  Pointer to data to be passed to EnumFunc.  This provides a
way to pass non-global data to EnumFunc.  

  




Output :  

(routine)  -   Return status from this call - indicates either success
(NOERROR), or what the error is.  

  

  




 **See Also :**


**[ACL\_PRIVILEGES](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0007004A00E8002385255E3F00027E24)**


**[ACL\_LEVEL\_xxx](ACL_LEVEL_xxx.md)**


**[ACL\_FLAG\_xxx](ACL_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





