




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




**Initial Release 5.0.3**



**Function : Folders**



**NSFFolderGetIDTable** **- Get the
ID Table of notes in a folder.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFFolderGetIDTable(**  

      DHANDLE  hViewDB,  

      DHANDLE  hDataDB,  

      NOTEID  ViewNoteID,  

      DWORD  Flags,  

      DHANDLE \*hTable**);**



**Description :**



This
function gets the Note IDs of notes in a folder and returns the handle of the
ID Table. 


 


**Parameters :**



Input :  

hViewDB  -  The handle of the database that contains the view or folder.  

  

hDataDB  -  The handle of the database that contains the data notes.  For
folders this must reference the same database as hViewDB.  

  

ViewNoteID  -  The ID of the view or folder note in the database. Use
NIFFindView to obtain the note ID of a view or folder note given its name.  

  

  

Flags  -  DWORD containing DB\_GETIDTABLE\_xxx flags  

  




Output :  

(routine)  -  Return status from this call:  

  

NOERROR - Success  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

hTable  -  Address where the handle for the ID Table will be stored.   

  




 **See Also :**


**[DB\_GETIDTABLE\_xxx](DB_GETIDTABLE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





