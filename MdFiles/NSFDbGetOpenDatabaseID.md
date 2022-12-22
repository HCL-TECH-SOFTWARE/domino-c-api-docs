




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




**Initial Release 4.0**



**Function : Database**



**NSFDbGetOpenDatabaseID** **- Get a
unique ID for an open database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



DWORD
LNPUBLIC **NSFDbGetOpenDatabaseID(**  

      DBHANDLE  hDBU**);**



**Description :**



Returns a
unique 32-bit identifier for a database that is valid as long as any handle to
the database remains open.  The same identifier will be returned for all
handles that refer to the same database.  In particular, if NSFDbReopen() is
called, a new handle will be created for the database, but this identifer will
remain the same, providing a simple and efficient way to determine whether or
not two database handles refer to the same database.


 


After all
handles to the database have been closed and the database is opened, this
function may or may not return a different database identifier.


 


**Parameters :**



Input :  

hDBU  -  Handle to an open database.  

  




Output :  

(routine)  -  Open database ID.  

  

  




 **See Also :**


**[NSFDbClose](NSFDbClose.md)**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**


**[NSFDbReopen](NSFDbReopen.md)**



----------------------------------------------------------------------------------------------------------


 





