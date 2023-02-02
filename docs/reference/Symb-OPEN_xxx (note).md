##### Symbolic Value : Note
##### OPEN_xxx (note) - Controls the way NSFNoteOpen, NSFNoteOpenByUNID, NSFNoteOpenExt, or NSFDbCopyNoteExt opens a note.
---
##### #include <nsfnote.h>
 **OPEN_xxx (note)(**

	  OPEN_SUMMARY,
	  OPEN_NOVERIFYDEFAULT,
	  OPEN_EXPAND,
	  OPEN_NOOBJECTS,
	  OPEN_SHARE,
	  OPEN_MARK_READ,
	  OPEN_ABSTRACT,
|	  OPEN_RESPONSE_ID_TABLE);
**Description :**
These flags control the manner in which NSFNoteOpen, NSFNoteOpenByUNID, 
NSFNoteOpenExt, or NSFDbCopyNoteExt reads a note into memory.  This, in turn, 
controls what information about the note is available to you and how it is 
structured. 
**Parameters :**


**See Also :**
[NSFDbCopyNoteExt](D:/md_files/NSFDbCopyNoteExt.md)
[NSFNoteGetInfo](D:/md_files/NSFNoteGetInfo.md)
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
[NSFNoteOpenByUNID](D:/md_files/NSFNoteOpenByUNID.md)
[NSFNoteOpenExt](D:/md_files/NSFNoteOpenExt.md)
[NSFNoteSign](D:/md_files/NSFNoteSign.md)
---
