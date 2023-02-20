##### Symbolic Value : Note
##### NOTE_FLAG_xxx - Flags attatched to the header data of a Note
---
```
#include <nsfnote.h>
```
**Description :**

The note flags WORD is one of the members of the note header data . The various 
bits of the note flags WORD identify different attributes of the note. 

The NOTE_FLAG_READONLY bit indicates that the note is Read-Only for the current 
user. If a note contains an author names field, and the name of the user 
opening the document is not included in the author names field list, then  the 
NOTE_FLAG_READONLY bit is set in the note header data when that user opens the 
note.

The NOTE_FLAG_ABSTRACTED bit indicates that the note has been abstracted 
(truncated). This bit may be set if the database containing the note has 
replication settings set to "Truncate large documents and remove attachments".

You can use NOTE_FLAG_INCREMENTAL and NOTE_FLAG_INCREMENTAL_FULL in a database 
hook driver for NSFNoteUpdate to determine whether the note is a complete note 
or a partial note that is to be merged with the note on disk.  If the 
NOTE_FLAG_INCREMENTAL flag is set, have the database hook driver return 
ERR_NO_INCR_UPDATE so the replicator will retry with the full note 
(NOTE_FLAG_INCREMENTAL_FULL).

Use NSFNoteGetInfo to access note header data.   Specify _NOTE_FLAGS as the 
note header member ID to obtain the note flags for an open note.

**Sample Usage :**
```

NOTEHANDLE  hEditNOTE;
BOOL  fAbstracted;
WORD  NoteFlags;

NSFNoteGetInfo(hEditNOTE, _NOTE_FLAGS, &NoteFlags);

if (NoteFlags & NOTE_FLAG_ABSTRACTED)
{
    fAbstracted = TRUE;
}
```
**See Also :**
[NSFNoteGetInfo](/reference/Func/NSFNoteGetInfo)
[_NOTE_xxx](/reference/Symb/_NOTE_xxx)
---
