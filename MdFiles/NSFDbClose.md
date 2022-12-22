




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Function : Database**



**NSFDbClose** **- Closes a
database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbClose(**  

      DBHANDLE  hDB**);**



**Description :**



This
subroutine closes a previously opened database.  It is important to close
databases when you are through using them, since the close operation flushes
data structures to disk and cleans up memory space.


 


Note that
databases which have been closed by the C API may still be shown as "in
use" by the host operating system.  This can happen, for example, on a
server when a database has been opened by a server add-in program.


 


**Parameters :**



Input :  

hDB  -  The handle to the database that you want to close.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully closed the database.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  




 **Sample Usage :**


/\* Normal cleanup \*/  

if (error\_status = NSFDbClose(db\_handle\_src))  

  goto Exit;


else


  cleanup\_state -=
CLOSE\_SRC\_DB;


 **See Also :**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**



----------------------------------------------------------------------------------------------------------


 





