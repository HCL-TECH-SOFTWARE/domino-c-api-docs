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
**Description :**

These flags control the manner in which NSFNoteOpen, NSFNoteOpenByUNID, 
NSFNoteOpenExt, or NSFDbCopyNoteExt reads a note into memory.  This, in turn, 
controls what information about the note is available to you and how it is 
structured. 

**Parameters :**



**See Also :**
[NSFDbCopyNoteExt](/reference/Func/NSFDbCopyNoteExt)
[NSFNoteGetInfo](/reference/Func/NSFNoteGetInfo)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
[NSFNoteOpenByUNID](/reference/Func/NSFNoteOpenByUNID)
[NSFNoteOpenExt](/reference/Func/NSFNoteOpenExt)
[NSFNoteSign](/reference/Func/NSFNoteSign)
---
