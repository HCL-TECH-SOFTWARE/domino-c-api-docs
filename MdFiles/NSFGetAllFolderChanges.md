




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




**Initial Release 6.0.3**



**Function : Database; Folders**



**NSFGetAllFolderChanges** **- Get all
folder changes.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFGetAllFolderChanges(**  

      DHANDLE  hViewDB,  

      DHANDLE  hDataDB,  

      TIMEDATE \*Since,  

      DWORD  Flags,  

      NSFGETALLFOLDERCHANGESCALLBACK  Callback,  

      void \*Param,  

      TIMEDATE \*Until**);**



**Description :**



This
function will get all folder changes for a specific time period and call the
callback routine for each change.


 


**Parameters :**



Input :  

hViewDB  -  Handle of the database that contains the folders.  

  

hDataDB  -  Handle to the database that contains the data notes.  This must
reference the same database as hViewDB.  

  

Since  -  A pointer to a TIMEDATE structure containing a time/date value specifying
the earliest time the folder was modified.  

  

Flags  -  Flags.  

  

Callback  -  The get all folder changes callback function pointer.  This
function is called for each folder change.  See NSFGETALLFOLDERCHANGESCALLBACK.  

  

Param  -  Callback parameter.  See NSFGETALLFOLDERCHANGESCALLBACK.  

  

Until  -  A pointer to a TIMEDATE structure containing a time/date value
specifying the latest time the folder was modified.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_xxx - Errors returned by lower level functions.  Call OSLoadString to
interpret the error code for display.  

  

  




 **See Also :**


**[NSFGETALLFOLDERCHANGESCALLBACK](NSFGETALLFOLDERCHANGESCALLBACK.md)**



----------------------------------------------------------------------------------------------------------


 





