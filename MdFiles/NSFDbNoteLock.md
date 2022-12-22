




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



**NSFDbNoteLock** **- Lock a
note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFDbNoteLock(**  

      DBHANDLE  hDB,  

      NOTEID  NoteID,  

      DWORD  Flags,  

      char \*pLockers,  

      DHANDLE \*rethLockers,  

      DWORD \*retLength**);**



**Description :**



This
function adds an "authors" field to a note which contains a list of
"writers" who will be able to update the note.  Any user will be able
to open the note, but only the members contained in the "authors"
field are allowed to update the note.  


 


This
function will only succeed if the database option "Allow document
locking" is set.  Please refer to the Domino documentation for a full
description of document locking.


 


**Parameters :**



Input :  

hDB  -  The handle of the open database that contains the note to be locked.  

  

NoteID  -  The ID of the note that you want to lock.  

  

Flags  -  Flags to control how a note is locked.  See NOTE\_LOCK\_xxx.  

  

pLockers  -  A pointer to a null-terminated character string containing the
name or names to be added to the authors field.  Multiple names must be
delimited by a semi-colon (;).  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Success.  

  

ERR\_NOTE\_LOCKED - The note is already locked.  You can determine who locked the
note by setting the NOTE\_LOCK\_STATUS flag  and using the rethLockers parameter.  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, etc.).  There are so many possible causes, that It is best to use
the code in a call to OSLoadString and display/log the error for the user as
your default error handling.  

  

  

rethLockers  -  If the note is already locked and you specify the
NOTE\_LOCK\_STATUS flag, this is the handle to the "lockers".  

  

retLength  -  Length of the string associated with rethLockers.  

  




 **See Also :**


**[NSFDbNoteUnlock](NSFDbNoteUnlock.md)**



----------------------------------------------------------------------------------------------------------


 





