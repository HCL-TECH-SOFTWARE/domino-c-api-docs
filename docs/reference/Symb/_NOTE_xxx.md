##### Symbolic Value : Note
##### _NOTE_xxx - Note header member IDs used to get/set portions of a Note's header.
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	_NOTE_DB	  -  Get/set the Database handle (DBHANDLE).

	_NOTE_ID	  -  Get/set the Note ID (NOTEID).

	_NOTE_OID	  -  Get/set the Originator ID (OID).

	_NOTE_CLASS	  -  Get/set the NOTE_CLASS (WORD).

	_NOTE_MODIFIED	  -  Get/set the Modified in this file time/date (TIMEDATE : GMT normalized).

	_NOTE_PRIVILEGES	  -  Obsolete in Notes 3.0 [Notes 2.X: Get/set the Access Control List (ACL) privileges associated with manipulating this Note(WORD). Only the low order 5 bits of the WORD used in Notes 2.X. Bit 0 = privilege 1, bit 1 = privilege 2, bit 2 = privilege 3, bit 3 = privilege 4, and bit 4 = privilege 5.]

	_NOTE_FLAGS	  -  Get/set the note flags (WORD). See NOTE_FLAG_xxx.

	_NOTE_ACCESSED	  -  Get/set the Accessed in this file date (TIMEDATE).

	_NOTE_PARENT_NOTEID	  -  Get the Note ID of the immediate parent note for this note (NOTEID). This ID is zero if this note has no parent.

	_NOTE_RESPONSE_COUNT	  -  Get the number of immediate response notes for this note (DWORD).

	_NOTE_RESPONSES	  -  Get a handle to the ID Table of Note IDs of the immediate responses of this note (HANDLE). If a note has no responses, NULLHANDLE is returned. There is no ordering of the response Note IDs in the table. The OPEN_RESPONSE_ID_TABLE flag must be specified when the note is opened in order to obtain a valid ID Table handle. If the OPEN_RESPONSE_ID_TABLE flag is not specified when the note is opened, NULLHANDLE will be returned as the value of the ID Table handle. Do not explicityly deallocate the ID Table. It will be deallocated by NSFNoteClose().

	_NOTE_ADDED_TO_FILE	  -  For AddedToFile time.

	_NOTE_OBJSTORE_DB	  -  DBHANDLE of object store used by linked items.


**Description :**

Use these IDs to get or set particular members of a Note's header structure.<br>
<br>
Opening a note reads the note header into memory. Use the note handle to refer to the in-memory note header. The note header data includes the Note ID, the handle to the associated database, the Note Originator ID, the note class, and the modified time/date. Closing a note frees the memory containing the note header.<br>
<br>
Get any member of the note header by calling NSFNoteGetInfo with the appropriate note member ID. Set any member of the note header by calling NSFNoteSetInfo. <br>
<br>
Warning: changing a note's header data in memory via NSFNoteSetInfo does not change the note's header data on disk. NSFNoteUpdate overwrites some of a note's header data when it writes a note from memory to disk. For example, you can not change the _NOTE_MODIFIED time/date of a note on disk via NSFNoteSetInfo, because NSFNoteUpdate always sets the modified time/date when it writes the note to disk, over-writing whatever was previously stored in the note header.<br>
<br>
Use _NOTE_DB to reference to the handle of the database asociated with the note. Changing the database handle causes NSFNoteUpdate to save the note to the corresponding database. The referenced database must be open.<br>
<br>
Use _NOTE_ID to reference the Note ID. Create a new note in the database by zeroing the note ID in the header before updating the note to the database.<br>
<br>
Use _NOTE_OID to reference the Originator ID. Generate a new OID and set the OID in the header before updating the note to ensure the new note has a unique Originator ID.  A Domino database must not contain more than one note with the same UNID portion of the OID. NSFNoteUpdate sets the SequenceTime member of the OID and increments the Sequence number.<br>
<br>
Use _NOTE_MODIFIED to reference the time/date when the note was last modified in this database by editing and saving. Note that NSFNoteUpdate sets the modified time/date when the note is written to disk, overwriting the value set in the note header.<br>
<br>
Use _NOTE_FLAGS to reference the note header flags. These flags identify the note as Read-only or abstracted (see NOTE_FLAG_xxx).<br>
<br>
Use _NOTE_ACCESSED to reference the last accessed date of the document in this database.   The Domino function @Accessed yields this same value.<br>
<br>
	_NOTE_PARENT_NOTEID, _NOTE_RESPONSE_COUNT, and _NOTE_RESPONSES are used to access response hierarchy information with NSFNoteGetInfo().  The response hierarchy is a tree structure of main notes, responses, and responses-to-responses in a Domino database.  It does not include categories that can be defined in a view.  Only data notes appear in the response hierarchy.  Non-data notes, such as a view note, will always return a parent Note ID value of zero, a response count value of zero, and a response ID Table handle value of NULLHANDLE.  Response hierarchy information is available only on notes that have been created or modified with Domino or Notes Release 4 and later.  These note header member IDs must not be used with NSFNoteSetInfo().  The only way to update the structure of the response hierarchy in a Domino database is by creating or deleting notes, or by creating, deleting, or modifying a $REF item in a note which points to the parent of that note.<br>
<br>
	The parent Note ID (obtained by using _NOTE_PARENT_NOTEID) and the response count (obtained by using _NOTE_RESPONSE_COUNT) are always made available to an application whenever a note is opened.  The ID Table of responses (obtained by using _NOTE_RESPONSES) is available to an application only if the OPEN_RESPONSE_ID_TABLE flag is specified when the note was opened; otherwise, a value of NULLHANDLE is returned.


**Sample Usage :**
```

    NOTEHANDLE      hOldNote;
    NOTEHANDLE      hNewNote;
    STATUS          error;
    OID             oidNew;

    if (error = NSFNoteOpen (
            *(DBHANDLE*)db_handle,
            NoteID,
            0,            /* open flags */
            &hOldNote))        /* note handle (return) */
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

    if (error = NSFDbGenerateOID(*(DBHANDLE*)db_handle, &oidNew))
    {
        printf("Error: unable to generate new OID.\n");
        NSFNoteClose(hNewNote);
        NSFNoteClose(hOldNote);
        return(ERR(error));
    }
   
    NSFNoteSetInfo(hNewNote, _NOTE_ID, NULL);
    NSFNoteSetInfo(hNewNote, _NOTE_OID, &oidNew);
    NSFNoteSetInfo(hNewNote, _NOTE_DB, &db_handle2);

    if (error = NSFNoteUpdate (hNewNote, UPDATE_FORCE))
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

```

**See Also :**
[NOTE_CLASS_xxx](/domino-c-api-docs/reference/Symb/NOTE_CLASS_xxx)
[NOTE_FLAG_xxx](/domino-c-api-docs/reference/Symb/NOTE_FLAG_xxx)
[NSFDbGenerateOID](/domino-c-api-docs/reference/Func/NSFDbGenerateOID)
[NSFNoteGetInfo](/domino-c-api-docs/reference/Func/NSFNoteGetInfo)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[NSFNoteSetInfo](/domino-c-api-docs/reference/Func/NSFNoteSetInfo)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
---
