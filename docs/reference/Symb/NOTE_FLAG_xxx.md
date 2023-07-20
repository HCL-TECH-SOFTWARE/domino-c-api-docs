##### Symbolic Value : Note
##### NOTE_FLAG_xxx - Flags attatched to the header data of a Note
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	NOTE_FLAG_READONLY	  -  TRUE if document cannot be updated

	NOTE_FLAG_ABSTRACTED	  -  Document is missing some data (truncated)

	NOTE_FLAG_INCREMENTAL	  -  Incremental note (place holders). This is an incomplete note (the note is a field level replication type note).

	NOTE_FLAG_LINKED	  -  Note contains linked items or linked objects.

	NOTE_FLAG_INCREMENTAL_FULL	  -  Incremental type note Fully opened (NO place holders). This type of note is meant to retain the Item sequence numbers.

	NOTE_FLAG_CANONICAL	  -  Note is open in canonical form. Data types and data values that are normally converted to host format are left unconverted.


**Description :**

The note flags WORD is one of the members of the note header data . The various bits of the note flags WORD identify different attributes of the note. <br>
<br>
The NOTE_FLAG_READONLY bit indicates that the note is Read-Only for the current user. If a note contains an author names field, and the name of the user opening the document is not included in the author names field list, then  the NOTE_FLAG_READONLY bit is set in the note header data when that user opens the note.<br>
<br>
The NOTE_FLAG_ABSTRACTED bit indicates that the note has been abstracted (truncated). This bit may be set if the database containing the note has replication settings set to &quot;Truncate large documents and remove attachments&quot;.<br>

<ul><br>
You can use NOTE_FLAG_INCREMENTAL and NOTE_FLAG_INCREMENTAL_FULL in a database hook driver for NSFNoteUpdate to determine whether the note is a complete note or a partial note that is to be merged with the note on disk.  If the NOTE_FLAG_INCREMENTAL flag is set, have the database hook driver return ERR_NO_INCR_UPDATE so the replicator will retry with the full note (NOTE_FLAG_INCREMENTAL_FULL).<br>
<br>
Use NSFNoteGetInfo to access note header data.   Specify _NOTE_FLAGS as the note header member ID to obtain the note flags for an open note.</ul>



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
[NSFNoteGetInfo](/domino-c-api-docs/reference/Func/NSFNoteGetInfo)
[_NOTE_xxx](/domino-c-api-docs/reference/Symb/_NOTE_xxx)
---
