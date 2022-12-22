




<!--
 /\* Font Definitions \*/
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




**Initial Release 6.0.2**



**Function : Database**



**NSFDbDeleteExtended** **- Delete a
database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbDeleteExtended(**  

      cost char far \*PathName,  

      DHANDLE  hNameList**);**



**Description :**



This
function deletes a specified Domino database using the path specification
provided and allows for a NAMES\_LIST structure UserName to provide
authentication for trusted servers.


 


**Parameters :**



Input :  

PathName  -  The address of a text buffer containing a database name or
alternately, a full network path specification to the database built with
OSPathNetConstruct.  The database file name should be a null-terminated string.  

  

hNameList  -  May be NULLHANDLE or a HANDLE to a NAMES\_LIST structure that
contains a UserName that is used to provide authentication for trusted
servers.  This causes the UserName's ACL permissions in the database to be
enforced.  Please see NSFBuildNamesList for more information on building a
NAMES\_LIST structure.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - database successfully deleted.  

ERR\_NOACCESS - You are not authorized to perform that operation  

ERR\_NOEXIST -  File does not exist  

ERR\_DRIVE\_NOT\_READY - Drive is not ready  

ERR\_LOCK - File cannot be shared while in use by another process  

ERR\_IOERROR - I/O data error  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[NSFDbDelete](NSFDbDelete.md)**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**



----------------------------------------------------------------------------------------------------------


 





