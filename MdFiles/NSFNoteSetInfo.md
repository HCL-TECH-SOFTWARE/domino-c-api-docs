




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



**NSFNoteSetInfo** **- Sets the
specified value of in-memory note header.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



void
LNPUBLIC **NSFNoteSetInfo(**  

      NOTEHANDLE  note\_handle,  

      WORD  note\_member,  

      void far \*value\_ptr**);**



**Description :**



This function
sets the specified portion of a note header in memory to a particular value.
The value set by this function resides only in memory. Call NSFNoteUpdate() to
write the changes from memory to the database file on disk. If NSFNoteUpdate()
is not called before closing the note, the value set by NSFNoteSetInfo() will
be lost.  

  

Use NSFNoteSetInfo() with \_NOTE\_ID to set the note ID of an in-memory note to
zero. NSFNoteUpdate() will create a new note in the database if the note ID is
zero.  

  

Use NSFNoteSetInfo() with \_NOTE\_DB to associate the in-memory note with a
particular database handle. NSFNoteUpdate() will write the in-memory note to
the associated database. The database must be open.  

  

Use NSFNoteSetInfo() with \_NOTE\_OID to set the Originator ID of an in-memory
note to a value generated with NSFDbGenerateOID() to avoid storing more than
one note with the same UNID in a single database. The UNID is part of the OID.
A Domino database must not contain more than one note with the same UNID.   

  

NSFNoteUpdate() sets the SequenceTime (part of the OID) when writing the note
to disk, over-writing any value you may have set using NSFNoteSetInfo. It also
increments the sequence number. NSFNoteUpdate() also sets the note modification
time when writing a note to disk. Any value stored in memory by calling
NSFNoteSetInfo with \_NOTE\_MODIFIED is over written by NSFNoteUpdate.


 


**Parameters :**



Input :  

note\_handle  -  The handle of an open note.  

  

note\_member  -  A WORD containing the note member ID (see \_NOTE\_xxx) for the
note header value you wish to set.  

  

value\_ptr  -  A pointer to a value which will be the new value of specified
portion of the note header.  If NULL is specified, then the desired value in
the note will be zeroed.  

  




Output :  

(routine)  -  None.  

  

  




 **Sample Usage :**


  

   /\* Update Note Info as if an edit had been made \*/  

       if (error\_status = NSFDbGenerateOID(db\_handle\_dst, &new\_oid))  

           goto Exit;  

       NSFNoteSetInfo(note\_handle, \_NOTE\_OID, &new\_oid);  

  

    if (error\_status = NSFNoteUpdate(note\_handle, 0))  

        goto Exit;  

  

  




 **See Also :**


**[NSFDbGenerateOID](NSFDbGenerateOID.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteCopy](NSFNoteCopy.md)**


**[NSFNoteGetInfo](NSFNoteGetInfo.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[\_NOTE\_xxx](_NOTE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





