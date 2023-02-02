##### Function : Note
##### NSFNoteUpdate - Write in-memory note to on-disk database.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteUpdate(**

	NOTEHANDLE  note_handle,
	WORD  update_flags);
**Description :**
This function writes the in-memory version of a note to its database. Prior to 
issuing this call, a new note (or changes to a note) are not a part of the 
on-disk database.  This function only supports the set of 16-bit WORD options 
described in the entry UPDATE_xxx;  to use the extended 32-bit DWORD options, 
use the function NSFNoteUpdateExtended().

You should also consider updating the collections associated with other Views 
in a database via the function NIFOpenCollection or NIFUpdateCollection, if you 
have added and/or deleted a substantial number of documents.  If the Server's 
Indexer Task does not rebuild the collections associated with the database's 
Views,  the first user to access a View in the modified database might 
experience an inordinant delay, while the collection is rebuilt by the Notes 
Workstation (locally) or Server Application (remotely).

Do not update notes to disk that contain invalid items.  An example of an 
invalid item is a view design note that has a $Collation item whose BufferSize 
member is set to zero.  NSFNoteUpdate may return an error for an invalid item 
that was not caught in a previous release of Domino or Notes.

	Note: if you have enabled IMAP on a database, in the case of the 
special NoteID "NOTEID_ADD_OR_REPLACE", a new note is always created.
**Parameters :**
Input :
note_handle  -  The handle of the note that you want to update.

update_flags  -  Flags that control the manner in which the note update is done. The flags are defined in UPDATE_xxx and may be or'ed together to combine functionality.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_DATA_ONLY
ERR_UPDATE_CLASS
ERR_VERSION
ERR_CONFLICT
ERR_NOT_AUTHOR
ERR_NEW_NAME_KEY

ERR_SUMMARY_TOO_BIG -  "Field is too large (32K) or field's column in selection formula is too large".  You have appended more than about 16184 bytes to this note in items that have the ITEM_SUMMARY flag set. API functions such as NSFItemSetText set the ITEM_SUMMARY flag by default. Work around this problem by using NSFItemAppend to append some of these fields to the note without setting the ITEM_SUMMARY flag in the item_flags argument to NSFItemAppend. 


**Sample Usage :**
```
if (error_status = NSFNoteUpdate(note_handle, 0))
           goto Exit;
```
**See Also :**
[ITEM_xxx](D:/md_files/ITEM_xxx.md)
[NIFOpenCollection](D:/md_files/NIFOpenCollection.md)
[NIFUpdateCollection](D:/md_files/NIFUpdateCollection.md)
[NSFItemAppend](D:/md_files/NSFItemAppend.md)
[NSFNoteClose](D:/md_files/NSFNoteClose.md)
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
[UPDATE_xxx](D:/md_files/UPDATE_xxx.md)
[NSFNoteUpdateExtended](D:/md_files/NSFNoteUpdateExtended.md)
---
