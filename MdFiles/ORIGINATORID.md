




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




 


**Data Type : IDs**



**ORIGINATORID** **-** Uniquely
identifies all replicas of the same note.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct
ORIGINATORID\_tag {  

    DBID          File;            

    TIMEDATE      Note;           

    DWORD         Sequence;  

    TIMEDATE      SequenceTime;  

} ORIGINATORID;


 


**Description :**



The
Originator ID (OID) for a note identifies all replica copies of the same note
and distinguishes between different revisions of that note.  The Originator ID
is composed of two parts:  (1)  the Universal Note ID (UNID) and (2) the
Sequence Number and Sequence Time.   

  

The UNID (the first part of the OID) universally identifies all copies of the
same note. If one note in one database has the same UNID as another note in a
replica of that database, then the two notes are replica copies of each other.
The Sequence Number and the Sequence Time, taken together, distinguish
different revisions of the same note from one another.   

  

The full Originator ID uniquely identifies one particular version of a note. A
modified version of a replica copy of a particular note will have a different
OID. This is because Domino or Notes increments the Sequence Number when a note
is edited, and also sets the Sequence Time to the timedate when the Sequence
Number was incremented.  This means that when one replica copy of a note
remains unchanged, but another copy is edited and modified, then the UNIDs of
the 2 notes will remain the same but the Sequence Number and Sequence Times
(hence, the OIDs) will be different.  

  

The "File" member of the OID (and UNID), contains a number derived in
different ways depending on the release of Domino or Notes.  Pre- 2.1 versions
of Notes set the "File" member to the creation timedate of the NSF
file in which the note is created. Notes 2.1 sets the "File" member
to a user-unique identifier, derived in part from information in the ID of the
user creating the note, and in part from the database where the note is
created. Notes 3.0 sets the "File" member to a random number
generated at the time the note is created.  

  

The "Note" member of the OID (and UNID), contains the date/time when
the very first copy of the note was stored into the first NSF (Note: date/time
from $CREATED item, if exists, takes precedence).  

  

The "Sequence" member is a sequence number used to keep track of the
most recent version of the note. The "SequenceTime" member is a
sequence number qualifier, that allows the Domino replicator to determine which
note is later given identical Sequence numbers.   The sequence time qualifies
the sequence number by preventing two concurrent updates from looking like no
update at all. The sequence time also forces all Domino systems to reach the
same decision as to which update is the "latest" version.  The
sequence time is the value that is returned to the @Modified formula and
indicates when the document was last edited and saved.  

  

API programs may obtain the Originator ID from the handle of an existing, open
note by specifying the \_NOTE\_OID member ID in the NSFNoteGetInfo function. See
the example below. API programs may also obtain the OID for a note given the
Note ID by using the NSFDbGetNoteInfo function.  If you need to make an
existing note appear to be a totally new note, the NSFDbGenerateOID function
can be used to generate a new OID.


 **Sample Usage :**


  

   ORIGINATORID    NoteOID;  

  

      /\*  

     \* Get the OID from the note AFTER it has been updated  

     \*/  

  

    NSFNoteGetInfo (hNote, \_NOTE\_OID, &NoteOID);  

  




 **See Also :**


**[NSFDbGenerateOID](NSFDbGenerateOID.md)**


**[NSFDbGetNoteInfo](NSFDbGetNoteInfo.md)**


**[NSFNoteGetInfo](NSFNoteGetInfo.md)**


**[NSFNoteSetInfo](NSFNoteSetInfo.md)**


**[OID](OID.md)**


**[UNID](UNID.md)**


**[UNIVERSALNOTEID](UNIVERSALNOTEID.md)**


**[\_NOTE\_xxx](_NOTE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





