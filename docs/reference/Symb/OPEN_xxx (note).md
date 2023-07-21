##### Symbolic Value : Note
##### OPEN_xxx (note) - Controls the way NSFNoteOpen, NSFNoteOpenByUNID, NSFNoteOpenExt, or NSFDbCopyNoteExt opens a note.
---
```
#include <nsfnote.h>
 OPEN_xxx (note)(

	  OPEN_SUMMARY,
	  OPEN_NOVERIFYDEFAULT,
	  OPEN_EXPAND,
	  OPEN_NOOBJECTS,
	  OPEN_SHARE,
	  OPEN_MARK_READ,
	  OPEN_ABSTRACT,
|	  OPEN_RESPONSE_ID_TABLE);
```

**Symbolic Values :**

	OPEN_SUMMARY	  -  Read only summary information.

	OPEN_NOVERIFYDEFAULT	  -  Do not verify if this is the default note in this class. A note is a default note if the NOTE_CLASS_DEFAULT bit is OR'd into the note class. Normally, if the NOTE_CLASS_DEFAULT bit is OR'd into the note class, then NSFNoteOpen or NSFNoteOpenByUNID will check this note against a default note table in the database and verify that the note being opened is still the default note for that class. If this flag is set, then such verification will not occur. This flag saves one disk I/O if the note is marked as being the "default note", in the event that this information is not desired.

	OPEN_EXPAND	  -  For fields of TYPE_TEXT, expand the data to 1-entry TYPE_TEXT_LIST values while reading the note. For fields of TYPE_NUMBER, expand the data to TYPE_NUMBER_RANGE. For fields of TYPE_TIME, expand the data to TYPE_TIME_RANGE. This option is necessary if the note is to be signed or a signature verified; please see the entry for NSFNoteSign() for details.

	OPEN_NOOBJECTS	  -  Do not read any objects. Objects include file attachments and DDE links.Warning: documents opened with OPEN_NOOBJECTS then subsequently updated loose all objects that were previously attached.

	OPEN_SHARE	  -  Open in a "shared" memory mode.

	OPEN_CANONICAL	  -  Return ALL item values in canonical form, including the datatype WORD. API programs should not use this flag when explicitly calling NSFNoteOpen or NSFNoteOpenByUNID and must not use this flag when explicitly calling NSFDbCopyNoteExt. However, if the API program is a Domino database hook driver or an extension manager that accesses note item data over a network and the note was not opened by the API program itself, then it must check the OpenFlags parameter in the NoteOpen callback function (if the program is a database hook driver) or in the callback function for EM_NSFNOTEOPEN or EM_NSFNOTEOPENBYUNID (if the program is an extension manager) to see whether this flag is set. If this flag is set, use ODSReadMemory to convert any canonical data to host data. This can also be checked by calling NSFNoteGetInfo () with the header member _NOTE_FLAGS, and checking the flags for the presence of NOTE_FLAG_CANONICAL.

	OPEN_MARK_READ	  -  Mark unread to read if unread list is currently associated (database is a remote database).

	OPEN_ABSTRACT	  -  Only open an abstract of large documents.

	OPEN_RESPONSE_ID_TABLE	  -  Generate an ID Table of Note IDs for the responses to this note. Use this option in order to access the Note IDs of the immediate responses to a given note in a later call to NSFNoteGetInfo() using _NOTE_RESPONSES as the note header member ID.

	OPEN_WITH_FOLDERS	  -  Include folder objects - the default is not to. Folder objects appear in Folder notes. Folder notes contain two folder object items. The names of these items are VIEW_FOLDER_IDTABLE and VIEW_FOLDER_OBJECT. Each of these items is of TYPE_OBJECT. In order to access these items you must open the note with this flag. This flag can only be used with functions that take DWORD OPEN_xxx(note) flags, such as NSFNoteOpenExt. You do not need to set this flag when calling NSFDbCopyNoteExt.

	OPEN_RAW_RFC822_TEXT	  -  If set, leave TYPE_RFC822_TEXT items in native format. Otherwise, convert to TYPE_TEXT/TYPE_TIME. This flag can only be used with functions that take DWORD OPEN_xxx(note) flags, such as NSFNoteOpenExt.

	OPEN_RAW_MIME_PART	  -  If set, leave TYPE_MIME_PART items in native format. Otherwise, convert to TYPE_COMPOSITE. This flag can only be used with functions that take DWORD OPEN_xxx(note) flags, such as NSFNoteOpenExt.

	OPEN_RAW_MIME	  -  (OPEN_RAW_RFC822_TEXT | OPEN_RAW_MIME_PART) This flag can only be used with functions that take 32-bit DWORD OPEN_xxx(note) flags, such as NSFNoteOpenExt.


**Description :**

These flags control the manner in which NSFNoteOpen, NSFNoteOpenByUNID, NSFNoteOpenExt, or NSFDbCopyNoteExt reads a note into memory.  This, in turn, controls what information about the note is available to you and how it is structured. 


**Parameters :**




**See Also :**
[NSFDbCopyNoteExt](/domino-c-api-docs/reference/Func/NSFDbCopyNoteExt)
[NSFNoteGetInfo](/domino-c-api-docs/reference/Func/NSFNoteGetInfo)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[NSFNoteOpenByUNID](/domino-c-api-docs/reference/Func/NSFNoteOpenByUNID)
[NSFNoteOpenExt](/domino-c-api-docs/reference/Func/NSFNoteOpenExt)
[NSFNoteSign](/domino-c-api-docs/reference/Func/NSFNoteSign)
---
