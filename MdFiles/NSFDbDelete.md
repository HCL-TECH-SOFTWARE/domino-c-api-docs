




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



**NSFDbDelete** **- Delete a
database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbDelete(**  

      cost char far \*PathName**);**



**Description :**



This
function deletes a specified Domino database using the path specification
provided.


 


**Parameters :**



Input :  

PathName  -  The address of a text buffer containing a database name or
alternately, a full network path specification to the database built with
OSPathNetConstruct.  The database file name should be a null-terminated string.  

  




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

  

  




 **Sample Usage :**


  

   if (cleanup\_state & DELETE\_DST\_DB)  /\* delete incomplete work \*/  

       if (cleanup\_status = NSFDbDelete(dst\_name))  

       {  

           OSLoadString(0, cleanup\_status, cleanup\_msg, LINEOTEXT-1);  

           printf("\nCleanup Error: %s\n", cleanup\_msg);  

       }  

  




 **See Also :**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**



----------------------------------------------------------------------------------------------------------


 





