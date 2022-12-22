




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



**\_NOTE\_xxx** **-** Note header
member IDs used to get/set portions of a Note's header.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      \_NOTE\_DB   -  Get/set the Database handle (DBHANDLE).  

  

      \_NOTE\_ID    -  Get/set the Note ID (NOTEID).  

  

      \_NOTE\_OID             -  Get/set the Originator ID (OID).  

  

      \_NOTE\_CLASS        -  Get/set the NOTE\_CLASS (WORD).  

  

      \_NOTE\_MODIFIED   -  Get/set the Modified in this file time/date (TIMEDATE
: GMT normalized).  

  

      \_NOTE\_PRIVILEGES           -  Obsolete in Notes 3.0 [Notes 2.X: Get/set the
Access Control List (ACL) privileges associated with manipulating this
Note(WORD). Only the low order 5 bits of the WORD used in Notes 2.X. Bit 0 =
privilege 1, bit 1 = privilege 2, bit 2 = privilege 3, bit 3 = privilege 4, and
bit 4 = privilege 5.]  

  

      \_NOTE\_FLAGS        -  Get/set the note flags (WORD). See NOTE\_FLAG\_xxx.  

  

      \_NOTE\_ACCESSED             -  Get/set the Accessed in this file date
(TIMEDATE).  

  

      \_NOTE\_PARENT\_NOTEID   -  Get the Note ID of the immediate parent note for
this note (NOTEID). This ID is zero if this note has no parent.  

  

      \_NOTE\_RESPONSE\_COUNT           -  Get the number of immediate response
notes for this note (DWORD).  

  

      \_NOTE\_RESPONSES          -  Get a handle to the ID Table of Note IDs of
the immediate responses of this note (HANDLE). If a note has no responses,
NULLHANDLE is returned. There is no ordering of the response Note IDs in the
table. The OPEN\_RESPONSE\_ID\_TABLE flag must be specified when the note is
opened in order to obtain a valid ID Table handle. If the
OPEN\_RESPONSE\_ID\_TABLE flag is not specified when the note is opened,
NULLHANDLE will be returned as the value of the ID Table handle. Do not
explicityly deallocate the ID Table. It will be deallocated by NSFNoteClose().  

  

      \_NOTE\_ADDED\_TO\_FILE    -  For AddedToFile time.  

  

      \_NOTE\_OBJSTORE\_DB      -  DBHANDLE of object store used by linked items.  

  




**Description :**



Use these
IDs to get or set particular members of a Note's header structure.  

  

Opening a note reads the note header into memory. Use the note handle to refer
to the in-memory note header. The note header data includes the Note ID, the
handle to the associated database, the Note Originator ID, the note class, and
the modified time/date. Closing a note frees the memory containing the note
header.  

  

Get any member of the note header by calling NSFNoteGetInfo with the
appropriate note member ID. Set any member of the note header by calling
NSFNoteSetInfo.   

  

Warning: changing a note's header data in memory via NSFNoteSetInfo does not
change the note's header data on disk. NSFNoteUpdate overwrites some of a note's
header data when it writes a note from memory to disk. For example, you can not
change the \_NOTE\_MODIFIED time/date of a note on disk via NSFNoteSetInfo,
because NSFNoteUpdate always sets the modified time/date when it writes the
note to disk, over-writing whatever was previously stored in the note header.  

  

Use \_NOTE\_DB to reference to the handle of the database asociated with the
note. Changing the database handle causes NSFNoteUpdate to save the note to the
corresponding database. The referenced database must be open.  

  

Use \_NOTE\_ID to reference the Note ID. Create a new note in the database by
zeroing the note ID in the header before updating the note to the database.  

  

Use \_NOTE\_OID to reference the Originator ID. Generate a new OID and set the
OID in the header before updating the note to ensure the new note has a unique
Originator ID.  A Domino database must not contain more than one note with the
same UNID portion of the OID. NSFNoteUpdate sets the SequenceTime member of the
OID and increments the Sequence number.  

  

Use \_NOTE\_MODIFIED to reference the time/date when the note was last modified
in this database by editing and saving. Note that NSFNoteUpdate sets the
modified time/date when the note is written to disk, overwriting the value set
in the note header.  

  

Use \_NOTE\_FLAGS to reference the note header flags. These flags identify the
note as Read-only or abstracted (see NOTE\_FLAG\_xxx).  

  

Use \_NOTE\_ACCESSED to reference the last accessed date of the document in this
database.   The Domino function @Accessed yields this same value.


 


      \_NOTE\_PARENT\_NOTEID,
\_NOTE\_RESPONSE\_COUNT, and \_NOTE\_RESPONSES are used to access response hierarchy
information with NSFNoteGetInfo().  The response hierarchy is a tree structure
of main notes, responses, and responses-to-responses in a Domino database.  It
does not include categories that can be defined in a view.  Only data notes
appear in the response hierarchy.  Non-data notes, such as a view note, will
always return a parent Note ID value of zero, a response count value of zero,
and a response ID Table handle value of NULLHANDLE.  Response hierarchy
information is available only on notes that have been created or modified with
Domino or Notes Release 4 and later.  These note header member IDs must not be
used with NSFNoteSetInfo().  The only way to update the structure of the
response hierarchy in a Domino database is by creating or deleting notes, or by
creating, deleting, or modifying a $REF item in a note which points to the
parent of that note.


 


      The
parent Note ID (obtained by using \_NOTE\_PARENT\_NOTEID) and the response count
(obtained by using \_NOTE\_RESPONSE\_COUNT) are always made available to an
application whenever a note is opened.  The ID Table of responses (obtained by
using \_NOTE\_RESPONSES) is available to an application only if the
OPEN\_RESPONSE\_ID\_TABLE flag is specified when the note was opened; otherwise, a
value of NULLHANDLE is returned.


 **Sample Usage :**


  

    NOTEHANDLE      hOldNote;  

    NOTEHANDLE      hNewNote;  

    STATUS          error;  

    OID             oidNew;  

  

    if (error = NSFNoteOpen (  

            \*(DBHANDLE\*)db\_handle,  

            NoteID,  

            0,            /\* open flags \*/  

            &hOldNote))        /\* note handle (return) \*/  

    {  

        printf("Error: unable to open note %lx.\n", NoteID);  

        return (ERR(error));  

    }  

  

    if (error = NSFNoteCopy(hOldNote, &hNewNote))  

    {  

        printf("Error: unable to copy note.\n");  

        NSFNoteClose(hOldNote);  

        return(ERR(error));  

    }  

  

    if (error = NSFDbGenerateOID(\*(DBHANDLE\*)db\_handle, &oidNew))  

    {  

        printf("Error: unable to generate new OID.\n");  

        NSFNoteClose(hNewNote);  

        NSFNoteClose(hOldNote);  

        return(ERR(error));  

    }  

     

    NSFNoteSetInfo(hNewNote, \_NOTE\_ID, NULL);  

    NSFNoteSetInfo(hNewNote, \_NOTE\_OID, &oidNew);  

    NSFNoteSetInfo(hNewNote, \_NOTE\_DB, &db\_handle2);  

  

    if (error = NSFNoteUpdate (hNewNote, UPDATE\_FORCE))  

    {  

        printf("Error: unable to update note to DB.\n");  

        NSFNoteClose(hNewNote);  

        return(ERR(error));  

    }  

  

    if (error = NSFNoteClose(hNewNote))  

    {  

        printf("Error: unable to close new note.\n");  

        return(ERR(error));  

    }  

  




 **See Also :**


**[NOTE\_CLASS\_xxx](NOTE_CLASS_xxx.md)**


**[NOTE\_FLAG\_xxx](NOTE_FLAG_xxx.md)**


**[NSFDbGenerateOID](NSFDbGenerateOID.md)**


**[NSFNoteGetInfo](NSFNoteGetInfo.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFNoteSetInfo](NSFNoteSetInfo.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**



----------------------------------------------------------------------------------------------------------


 





