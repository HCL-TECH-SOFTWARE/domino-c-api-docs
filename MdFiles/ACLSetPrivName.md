




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



**ACLSetPrivName** **- Given a
privilege number, set the given privilege name.**


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**



STATUS
LNPUBLIC **ACLSetPrivName(**  

      DHANDLE  hACL,  

      WORD  PrivNum,  

      char far \*PrivName**);**



**Description :**



This
function associates a privilege name (role) with a given privilege number (0
through ACL\_PRIVCOUNT - 1).   Privilege names associated with privilege numbers
0 through 4 are privilege levels compatible with versions of Notes prior to
Release 3.  When displayed by Notes or returned by ACLGetPrivName, they are
enclosed in parenthesis.  Privilege names associated with privilege numbers 5
through ACL\_PRIVCOUNT - 1 are members of the access role list.  When displayed
by Notes or returned by ACLGetPrivName, they are enclosed in brackets.


 


**Parameters :**



Input :  

hACL  -   Handle to an access control list.  

  

PrivNum  -  Privilege number (0 through ACL\_PRIVCOUNT - 1).  

  

PrivName  -   Pointer to the null-terminated privilege or role name string to
be associated with the given number.  Limited to ACL\_PRIVNAMEMAX characters,
including the null terminator.  

  




Output :  

(routine)  -   Return status from this call - indicates either success
(NOERROR), or what the error is.  

  

  




 **See Also :**


**[ACLGetPrivName](ACLGetPrivName.md)**



----------------------------------------------------------------------------------------------------------


 





