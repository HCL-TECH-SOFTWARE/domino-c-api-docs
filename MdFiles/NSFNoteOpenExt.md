




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 5.0**



**Function : Note**



**NSFNoteOpenExt** **- Opens a
note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteOpenExt(**  

      DBHANDLE  hDB,  

      NOTEID  NoteID,  

      DWORD  flags,  

      NOTEHANDLE \*rethNote**);**



**Description :**



This function
reads a note into memory and returns a handle to the in-memory copy.  Its input
is a database handle and a note ID within that database.  It is similar to
NSFNoteOpen with additional options for the flags parameter.  This function
allows using extended 32-bit DWORD update options, as described in the entry
OPEN\_xxx.


 


If the note
is marked as unread, by default this function does not change the unread mark. 
You can use the OPEN\_MARK\_READ flag to change an unread mark to read for remote
databases.  

  




Use
NSFNoteClose to close the note handle and deallocate the memory associated with
it.


 


**Parameters :**



Input :  

hDB  -  The handle of the open database that contains the note.  

  

NoteID  -  The ID of the note that you want to open.  

  

flags  -  Flags that control the manner in which the note is opened. This, in
turn, controls what information about the note is available to you and how it
is structured. The flags are defined in OPEN\_xxx (note) and may be or'ed
together to combine functionality.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_DIRECTORY  

ERR\_NOACCESS  

ERR\_INVALID\_ITEMUNK  

  

  

rethNote  -  The address of a NOTEHANDLE in which the handle of the opened note
is returned.  

  




 **Sample Usage :**


  

   /\* Reopen the Note and examine its contents \*/  

   if (error\_status = NSFNoteOpenExt(db\_handle, note1\_id,  

                                  0, &note1\_handle))  

       goto Exit;  

   else  

       cleanup\_state += CLOSE\_NOTE1;  

  




 **See Also :**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteCreate](NSFNoteCreate.md)**


**[NSFNoteOpenByUNID](NSFNoteOpenByUNID.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[OPEN\_xxx (note)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B660055DC1F)**



----------------------------------------------------------------------------------------------------------


 





