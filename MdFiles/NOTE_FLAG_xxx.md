




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




 


**Symbolic Value : Note**



**NOTE\_FLAG\_xxx** **-** Flags
attatched to the header data of a Note


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      NOTE\_FLAG\_READONLY    -  TRUE if document cannot be updated  

  

      NOTE\_FLAG\_ABSTRACTED            -  Document is missing some data
(truncated)  

  

      NOTE\_FLAG\_INCREMENTAL          -  Incremental note (place holders). This
is an incomplete note (the note is a field level replication type note).  

  

      NOTE\_FLAG\_LINKED          -  Note contains linked items or linked
objects.  

  

      NOTE\_FLAG\_INCREMENTAL\_FULL             -  Incremental type note Fully
opened (NO place holders). This type of note is meant to retain the Item
sequence numbers.  

  

      NOTE\_FLAG\_CANONICAL   -  Note is open in canonical form. Data types and
data values that are normally converted to host format are left unconverted.  

  




**Description :**



The note
flags WORD is one of the members of the note header data . The various bits of
the note flags WORD identify different attributes of the note.   

  

The NOTE\_FLAG\_READONLY bit indicates that the note is Read-Only for the current
user. If a note contains an author names field, and the name of the user
opening the document is not included in the author names field list, then  the
NOTE\_FLAG\_READONLY bit is set in the note header data when that user opens the
note.  

  

The NOTE\_FLAG\_ABSTRACTED bit indicates that the note has been abstracted
(truncated). This bit may be set if the database containing the note has
replication settings set to "Truncate large documents and remove
attachments".  

  




You can use
NOTE\_FLAG\_INCREMENTAL and NOTE\_FLAG\_INCREMENTAL\_FULL in a database hook driver
for NSFNoteUpdate to determine whether the note is a complete note or a partial
note that is to be merged with the note on disk.  If the NOTE\_FLAG\_INCREMENTAL
flag is set, have the database hook driver return ERR\_NO\_INCR\_UPDATE so the
replicator will retry with the full note (NOTE\_FLAG\_INCREMENTAL\_FULL).


  

Use NSFNoteGetInfo to access note header data.   Specify \_NOTE\_FLAGS as the
note header member ID to obtain the note flags for an open note.


 **Sample Usage :**


  

NOTEHANDLE  hEditNOTE;  

BOOL  fAbstracted;  

WORD  NoteFlags;  

  

NSFNoteGetInfo(hEditNOTE, \_NOTE\_FLAGS, &NoteFlags);  

  

if (NoteFlags & NOTE\_FLAG\_ABSTRACTED)  

{  

    fAbstracted = TRUE;  

}


 **See Also :**


**[NSFNoteGetInfo](NSFNoteGetInfo.md)**


**[\_NOTE\_xxx](_NOTE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





