##### Function : Note
##### NSFNoteSetInfo - Sets the specified value of in-memory note header.
---
```
#include <nsfnote.h>
void LNPUBLIC NSFNoteSetInfo(

	NOTEHANDLE  note_handle,
	WORD  note_member,
	void far *value_ptr);
```
**Description :**

This function sets the specified portion of a note header in memory to a 
particular value. The value set by this function resides only in memory. Call 
NSFNoteUpdate() to write the changes from memory to the database file on disk. 
If NSFNoteUpdate() is not called before closing the note, the value set by 
NSFNoteSetInfo() will be lost.

Use NSFNoteSetInfo() with _NOTE_ID to set the note ID of an in-memory note to 
zero. NSFNoteUpdate() will create a new note in the database if the note ID is 
zero.

Use NSFNoteSetInfo() with _NOTE_DB to associate the in-memory note with a 
particular database handle. NSFNoteUpdate() will write the in-memory note to 
the associated database. The database must be open.

Use NSFNoteSetInfo() with _NOTE_OID to set the Originator ID of an in-memory 
note to a value generated with NSFDbGenerateOID() to avoid storing more than 
one note with the same UNID in a single database. The UNID is part of the OID. 
A Domino database must not contain more than one note with the same UNID. 

NSFNoteUpdate() sets the SequenceTime (part of the OID) when writing the note 
to disk, over-writing any value you may have set using NSFNoteSetInfo. It also 
increments the sequence number. NSFNoteUpdate() also sets the note modification 
time when writing a note to disk. Any value stored in memory by calling 
NSFNoteSetInfo with _NOTE_MODIFIED is over written by NSFNoteUpdate.

**Parameters :**
Input :
note_handle  -  The handle of an open note.

note_member  -  A WORD containing the note member ID (see _NOTE_xxx) for the note header value you wish to set.

value_ptr  -  A pointer to a value which will be the new value of specified portion of the note header.  If NULL is specified, then the desired value in the note will be zeroed.

Output :
(routine)  -  None.



**Sample Usage :**
```

   /* Update Note Info as if an edit had been made */
       if (error_status = NSFDbGenerateOID(db_handle_dst, &new_oid))
           goto Exit;
       NSFNoteSetInfo(note_handle, _NOTE_OID, &new_oid);

    if (error_status = NSFNoteUpdate(note_handle, 0))
        goto Exit;


```
**See Also :**
[NSFDbGenerateOID](/reference/Func/NSFDbGenerateOID)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteCopy](/reference/Func/NSFNoteCopy)
[NSFNoteGetInfo](/reference/Func/NSFNoteGetInfo)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
[NSFNoteUpdate](/reference/Func/NSFNoteUpdate)
[_NOTE_xxx](/reference/Symb/_NOTE_xxx)
---
