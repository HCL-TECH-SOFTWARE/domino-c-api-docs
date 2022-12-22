




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



**NSFNoteCopy** **- Make an
in-memory copy of a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteCopy(**  

      NOTEHANDLE  note\_handle\_src,  

      NOTEHANDLE far \*note\_handle\_dst\_ptr**);**



**Description :**



This function
takes a handle to an open note, creates a duplicate copy in memory, and returns
a handle to the newly created note. The new copy has the same note header
information as the original, including the same Note ID, Originator ID, and
Database handle. Before calling NSFNoteUpdate to save the new copy, you must
generate an Originator ID, set the Originator ID, and zero the Note ID.   

  

Use NSFNoteCopy to create a new copy of a source note in the same database as
the source note. To copy the source note to a different database you may use
either NSFDbCopyNote or NSFNoteCopy. NSFDbCopyNote is more convenient for
copying many notes from one database to another, or when you have the Note IDs
of the source notes but do not wish to open the source notes. NSFNoteCopy is
more convenient if you have the source note open or if you will only be copying
one note.  Use NSFNoteClose to close the note handle and deallocate the memory
associated with it.  

  

To copy a note to a different database using NSFNoteCopy, you must generate a
new Originator ID, set the new Originator ID, zero the Note ID, and set the
Database handle to that of the destination database before saving the new copy
to the destination database. See the sample code below.  

  

Preserving the OID of the in-memory copy of a note makes it a replica copy of
the original note. A Domino database must not store two notes with the same
OID.


 


**Parameters :**



Input :  

note\_handle\_src  -  A NOTEHANDLE to a an existing note.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Note successfully copied.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  

note\_handle\_dst\_ptr  -  The address of a NOTEHANDLE  in which the handle to the
newly allocated note copy is returned.  

  




 **Sample Usage :**


/\* copy hOldNote to
destination database hNotesDB2.\*/  

    

  if (yerr=NSFNoteCopy(hOldNote,&hNewNote))  

  {  

     MessageBox(GetFocus(),"Unable to copy Note!",  

             "process one note",MB\_OK);  

     NSFNoteClose(hOldNote);  

     return(yerr);  

  }  

  

  

  if (yerr=NSFDbGenerateOID(hNotesDB2,&oidNew))  

  {  

     MessageBox(GetFocus(),"Unable to generate id!",  

             "process one note",MB\_OK);  

     NSFNoteClose(hNewNote);  

     NSFNoteClose(hOldNote);  

     return(yerr);  

  }  

  

  NSFNoteSetInfo(hNewNote,\_NOTE\_OID,&oidNew);  

  NSFNoteSetInfo(hNewNote,\_NOTE\_ID,NULL);  

  NSFNoteSetInfo(hNewNote,\_NOTE\_DB,&hNotesDB2);  

  

  

  if (yerr=NSFNoteUpdate(hNewNote,UPDATE\_FORCE))  

     MessageBox(GetFocus(),"Unable to update Note!",  

             "process one note",MB\_OK);


 **See Also :**


**[NSFDbCopyNote](NSFDbCopyNote.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteGetInfo](NSFNoteGetInfo.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFNoteSetInfo](NSFNoteSetInfo.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[\_NOTE\_xxx](_NOTE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





