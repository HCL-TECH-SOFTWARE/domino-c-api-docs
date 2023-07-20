##### Symbolic Value : Note
##### UPDATE_xxx - Flags to control how a note is updated or deleted.
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	UPDATE_FORCE	  -  Do an update or delete even if some other user has updated the note between the time the note was read into memory and the time we try to write it. This flag is appropriate for both updating and deleting a note.

	UPDATE_NAME_KEY_WARNING	  -  Give an error if the updated note contains a new field name that wasn't already defined in one of the forms in the database. This flag is appropriate for updating a note only.

	UPDATE_NOCOMMIT	  -  Do not flush all data to disk after the update. The note will be updated by the system, but non-summary data may not be immediately written to disk. This may improve the speed of NSFNoteUpdate if many operations are to be done sequentially, but risks loss of data if the machine crashes before data can be flushed to the disk. Summary data is always written to disk regardless of whether this flag is set or clear. This flag is appropriate for both updating and deleting a note.

	UPDATE_NOREVISION	  -  Do not maintain revision history. This flag is appropriate for updating a note only.

	UPDATE_NOSTUB	  -  Leave no trace of the note in the database if the note is deleted. This flag is only appropriate for deleting a note. You can use this flag on a deletion stub by removing the RRV_DELETED flag from the note id of the deletion stub before calling NSFNoteDelete or NSFNoteDeleteExtended. Once the deletion stub is removed, the deletion of the note will not be replicated. Otherwise, UPDATE_NOSTUB is only useful for applications that do NOT use views, and do not replicate. For example, a gateway may periodically examine a mail.box file, using NSFSearch and simply delete a document (using UPDATE_NOSTUB) when it's done with it. The database does not replicate, nor does it need views. UPDATE_NOSTUB ensures that there is minimum waste space allocated to stubs that are never needed in a highly volatile request-style database. Documents that are deleted with UPDATE_NOSTUB will still appear in the Domino views of the database and may cause problems when replicated. The documents themselves will not exist in the database and therefore cannot be opened.

	UPDATE_INCREMENTAL	  -  Compute incremental note info.

	UPDATE_DELETED	  -  The current update is a step in the process of deleting a note. API programs only use this flag in the context of a database hook driver. See Data Type DBHOOKVEC. Normally, API programs do not set this flag in calls to NSFNoteUpdate or NSFNoteDelete. NSFNoteDelete specifies this flag when it calls NSFNoteUpdate in the process of writing the deletion stub to the disk.

	UPDATE_DUPLICATES	  -  Obsolete. Allow duplicate items of the same name. This flag is appropriate for updating a note only.

	UPDATE_SHARE_SECOND	  -  Extended (32-bit DWORD) option: Split the second update of this note with the Note Object Store.

	UPDATE_SHARE_OBJECTS	  -  Extended (32-bit DWORD) option: Share only objects with the Note Object Store, not the summary information.


**Description :**

These flags control the manner in which Domino and Notes updates or deletes the on-disk copy of a note.  The extended (32-bit) options are ignored if passed to NSFNoteUpdate or NSFNoteDelete;  these options can only be passed to NSFNoteUpdatedExtended, NSFNoteDeleteExtended and NSFDbCopyNoteExt.


**See Also :**
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
[NSFNoteDelete](/domino-c-api-docs/reference/Func/NSFNoteDelete)
[NSFNoteUpdateExtended](/domino-c-api-docs/reference/Func/NSFNoteUpdateExtended)
[NSFNoteDeleteExtended](/domino-c-api-docs/reference/Func/NSFNoteDeleteExtended)
[NSFDbCopyNoteExt](/domino-c-api-docs/reference/Func/NSFDbCopyNoteExt)
---
