




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




 


**Function : Database; Access Control
List**



**NSFDbReadACL** **- Read in
the access control list of a database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbReadACL(**  

      DBHANDLE  hDB,  

      DHANDLE far \*rethACL**);**



**Description :**



This
function reads the access control list of a database into memory and returns a
handle to the in-memory copy.  All subsequent access to the access control list
is carried out via this handle.  If you modify this in-memory copy of the
access control list, use NSFDbStoreACL to store it in the database.


 


**Parameters :**



Input :  

hDB  -  Handle to the database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - success  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  

rethACL  -  Pointer to the returned handle to the access control list.  Use
OSMemFree to free the memory associated with this handle when this handle is
not longer needed for processing.  

  




 **See Also :**


**[ACLCreate](ACLCreate.md)**


**[NSFDbStoreACL](NSFDbStoreACL.md)**



----------------------------------------------------------------------------------------------------------


 





