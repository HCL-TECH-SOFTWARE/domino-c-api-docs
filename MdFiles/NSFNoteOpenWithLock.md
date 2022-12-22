




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



**NSFNoteOpenWithLock** **- Lock a
note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteOpenWithLock(**  

      DBHANDLE  hDB,  

      NOTEID  NoteID,  

      DWORD  LockFlags,  

      DWORD  OpenFlags,  

      char \*pLockers,  

      DHANDLE \*rethLockers,  

      DWORD \*retLength,  

      NOTEHANDLE far \*rethNote**);**



**Description :**



This
function will open a note, much like the function NSFNoteOpenExt, but it will
also add an "authors" field to a note which contains a list of
"writers" who will be able to update the note.  Any user will be able
to open the note, but only the members contained in the "authors"
field are allowed to update the note.


 


This
function will only succeed if the database option "Allow document
locking" is set.  Please refer to the Domino documentation for a full
description of document locking.


 


**Parameters :**



Input :  

hDB  -  The handle of the open database that contains the note.  

  

NoteID  -  The ID of the note that you want to open and lock.  

  

LockFlags  -  Flags to control how a note is locked.  See NOTE\_LOCK\_xxx.  

  

OpenFlags  -  Flags that control the manner in which the note is opened. This,
in turn, controls what information about the note is available to you and how
it is structured. The flags are defined in OPEN\_xxx (note) and may be or'ed
together to combine functionality.  

  

pLockers  -  A pointer to a null-terminated character string containing the
name or names to be added to the authors field.  

  




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

  

rethNote  -  The address of a NOTEHANDLE in which the handle of the opened note
is returned.  

  




 **See Also :**


**[NSFDbNoteLock](NSFDbNoteLock.md)**


**[NSFDbNoteUnlock](NSFDbNoteUnlock.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpenExt](NSFNoteOpenExt.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[OPEN\_xxx (note)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B660055DC1F)**



----------------------------------------------------------------------------------------------------------


 





