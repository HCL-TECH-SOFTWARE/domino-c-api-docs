




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




 


**Function : Note**



**NSFNoteCreate** **- Creates a
new in-memory note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteCreate(**  

      DBHANDLE  db\_handle,  

      NOTEHANDLE far \*note\_handle**);**



**Description :**



This
function creates a new note in memory. The note is empty after creation and is
not yet stored in the on-disk database. You may use NSFItemAppend to add fields
to the note, and NSFNoteUpdate to write the note to disk.  Use NSFNoteClose to
close the note handle and deallocate the memory associated with it.  

  




 


**Parameters :**



Input :  

db\_handle  -  The handle of the database in which you want to create a new
note.  

  




Output :  

(routine)  -  Return status from this call. Possible values:  

NOERROR - Note successfully created.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and display/log
the error for the user.  

  

  

note\_handle  -  The address of a NOTEHANDLE in which handle of the new empty
note is returned.  

  




 **Sample Usage :**


  

   /\* Create a Note in the specified database. \*/  

   if (error\_status = NSFNoteCreate(db\_handle, &note1\_handle))  

       goto Exit;  

   else  

       cleanup\_state += CLOSE\_NOTE1;  

  




 **See Also :**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[NSFNoteClose](NSFNoteClose.md)**



----------------------------------------------------------------------------------------------------------


 





