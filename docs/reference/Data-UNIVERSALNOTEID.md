##### Data Type : IDs
##### UNIVERSALNOTEID - Uniquely identifies a note across all databases.
---
##### #include <nsfdata.h>
**Description :**
The Universal Note ID (UNID) identifies all copies of the same note in 
different replicas of the same database universally (across all servers).  If 
one note in one database has the same UNID as another note in a replica 
database, then the two notes are replicas of each other.

The UNID is used to reference a specific note from another note. Specifically, 
the FIELD_LINK ($REF) field of a response note contains the UNID of it's 
parent.  Similarly, Doc Links (see NOTELINK) contains the UNID of the linked-to 
note plus the database ID where the linked-to note can be found. The important 
characteristic of the UNID is that it continues to reference a specific note 
even if the note being referenced is updated.

The Domino replicator uses the Universal Note ID to match the notes in one 
database with their respective copies in replica databases. For example, if 
database A is a replica copy of database B, database A contains a note with a 
particular UNID, and database B contains a note with the same UNID, then the 
replicator concludes that these two notes are replica copies of one another. On 
the other hand, if database A contains a note with a particular UNID but 
database B does not, then the replicator will create a copy of that note and 
add it to database B.  

One database must never contain two notes with the same UNID. If the replicator 
finds two notes with the same UNID in the same database, it generates an error 
message in the log and does not replicate the document.

The "File" member of the UNID contains a number derived in different ways 
depending on the release of Domino or Notes.  Pre- 2.1 versions of Notes set 
the "File" member to the creation timedate of the NSF file in which the note is 
created. Notes 2.1 sets the "File" member to a user-unique identifier, derived 
in part from information in the ID of the user creating the note, and in part 
from the database where the note is created.  Notes 3.0 sets the "File" member 
to a random number generated at the time the note is created.

The "Note" member of the UNID contains the date/time when the very first copy 
of the note was stored into the first NSF (Note: date/time from $CREATED item, 
if exists, takes precedence).
**Sample Usage :**
```

typedef struct 
{
    LIST ListHdr;
    UNID NoteUNID;
} RESPONSE;

RESPONSE   response;
OID        MainOID;

NSFNoteGetInfo (hNote, _NOTE_OID, &MainOID);

response.NoteUNID.File = MainOID.File;
response.NoteUNID.Note = MainOID.Note;

```
**See Also :**
[NOTELINK](D:/md_files/NOTELINK.md)
[OID](D:/md_files/OID.md)
[ORIGINATORID](D:/md_files/ORIGINATORID.md)
[UNID](D:/md_files/UNID.md)
[NSFNoteOpenByUNID](D:/md_files/NSFNoteOpenByUNID.md)
---
