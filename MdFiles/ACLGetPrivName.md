




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



**ACLGetPrivName** **- Given a
privilege number, get the privilege name.**


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**



STATUS
LNPUBLIC **ACLGetPrivName(**  

      DHANDLE  hACL,  

      WORD  PrivNum,  

      char far \*retPrivName**);**



**Description :**



This
function returns the privilege name (role) associated with a given  privilege
number (0 through ACL\_PRIVCOUNT - 1).  Privilege names associated with
privilege numbers 0 through 4 are privilege levels compatible with versions of
Notes prior to Release 3 and are enclosed in parenthesis.  Privilege names
associated with privilege numbers 5 through ACL\_PRIVCOUNT - 1 are members of
the access role list and are enclosed in brackets.


 


**Parameters :**



Input :  

hACL  -  Handle to an access control list.  

  

PrivNum  -  Privilege number (0 through ACL\_PRIVCOUNT - 1).  

  




Output :  

(routine)  -  Return status from this call - indicates either success
(NOERROR), or what the error is.  

  

  

retPrivName  -  Pointer to returned privilege or role name.  The buffer that
holds the privilege or role name must be at least ACL\_PRIVSTRINGMAX in size.  

  




 **See Also :**


**[ACLSetPrivName](ACLSetPrivName.md)**



----------------------------------------------------------------------------------------------------------


 





