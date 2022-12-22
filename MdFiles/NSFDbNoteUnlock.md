




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




**Initial Release 6**



**Function : Note**



**NSFDbNoteUnlock** **- Unlock a
note**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFDbNoteUnlock(**  

      DBHANDLE  hDB,  

      NOTEID  NoteID,  

      DWORD  Flags**);**



**Description :**



This
function removes the lock on a note.  Only the members contained in the
"writers" list are allowed to remove a lock, with the exception of
person(s) designated as capable of removing locks.  


 


Please refer
to the Domino documentation for a full description of document locking.


 


**Parameters :**



Input :  

hDB  -  The handle of the open database that contains the note to be unlocked.  

  

NoteID  -  The ID of the note that you want to unlock.  

  

Flags  -  Flags to control how a note is locked.  See NOTE\_LOCK\_xxx.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Success.  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, etc.).  There are so many possible causes, that It is best to use
the code in a call to OSLoadString and display/log the error for the user as
your default error handling.  

  

  




 **See Also :**


**[NSFDbNoteLock](NSFDbNoteLock.md)**



----------------------------------------------------------------------------------------------------------


 





