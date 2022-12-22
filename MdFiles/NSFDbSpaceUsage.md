




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



**NSFDbSpaceUsage** **- Returns
information about the usage of space in a database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbSpaceUsage(**  

      DBHANDLE  hDB,  

      DWORD far \*retAllocatedBytes,  

      DWORD far \*retFreeByes**);**



**Description :**



This function
returns the number of bytes allocated and the number of bytes free in a
specified database.  

  

The total size of  the number of bytes allocated plus the number of bytes free
will differ from the file system size of the database.  This is due to internal
rounding of the size up to the next 256K boundary.  Used and unused space is
also calculated in "chunks" of allocation granularity while the file
system size is determined in actual bytes.  

  

The percent of the database that is in use is the result of the number of bytes
allocated divided by the size of the database, multiplied by 100.


 


**Parameters :**



Input :  

hDB  -  Handle to the database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - success  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that  it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retAllocatedBytes  -  Pointer to the returned number of bytes allocated in the
database for data notes, form notes, view notes, etc.  

  

retFreeByes  -  Pointer to the returned number of bytes free in the database.  

  




 **Sample Usage :**


  

  DBHANDLE hNotesDB;  

  DWORD dwUsed;  

  DWORD dwFree;  

  STATUS error;  

    

  /\* code to open the database goes here \*/  

  ...  

  

  error = NSFDbSpaceUsage (hNotesDB, &dwUsed, &dwFree);  

  

  if (error != NOERROR)  

  {  

     NSFDbClose (hNotesDB);  

     return (ERR(error));  

  }  

  

  printf(  

     "Allocated:  %10lu;\t  Free:  %10lu;\t  In Use:  %10.2f%s",  

     dwUsed, dwFree, (float)dwUsed / (float)(dwFree + dwUsed) \* 100,
"%");  

  




 




----------------------------------------------------------------------------------------------------------


 





