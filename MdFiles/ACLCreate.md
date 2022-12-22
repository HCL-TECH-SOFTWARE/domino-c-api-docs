




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



**ACLCreate** **- Creates
an access control list.**


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**



STATUS
LNPUBLIC **ACLCreate(**  

      DHANDLE far \*rethACL**);**



**Description :**



This
function creates an access control list for a database and should only be used
when the API program creates a new database with NSFDbCreate.  Otherwise,
NSFDbReadACL should be used to read in an existing access control list. 
Databases created through Domino Designer or Notes will contain an access
control list.    

  

The returned handle is a handle to an in-memory copy of an ACL.  All subsequent
access to it is carried out via this handle.  Use NSFDbStoreACL to store the
in-memory copy of the ACL in the database.  Use OSMemFree to deallocate the
list.


 


**Parameters :**




Output :  

(routine)  -  Return status from this call - indicates either success
(NOERROR), or what the error is.  

  

  

rethACL  -  Pointer to returned handle to an access control list.  Use
OSMemFree to free the memory associated with this handle when this handle is
not longer needed for processing.  

  




 **See Also :**


**[NSFDbReadACL](NSFDbReadACL.md)**


**[NSFDbStoreACL](NSFDbStoreACL.md)**



----------------------------------------------------------------------------------------------------------


 





