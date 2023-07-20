##### Symbolic Value : Database
##### GETNOTES_xxx - Control flags for NSFDbGetNotes.
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	GETNOTES_PRESERVE_ORDER	  -  Preserve order of notes in NoteID list.

	GETNOTES_SEND_OBJECTS	  -  Send (copiable) objects along with note.

	GETNOTES_ORDER_BY_SIZE	  -  Order returned notes by (approximate) ascending size.

	GETNOTES_CONTINUE_ON_ERROR	  -  Continue to next on list if error encountered.

	GETNOTES_GET_FOLDER_ADDS	  -  Enable folder-add callback function after the note-level callback.

	GETNOTES_APPLY_FOLDER_ADDS	  -  Apply folder ops directly - don't bother using callback.

	GETNOTES_NO_STREAMING	  -  Don't stream - used primarily for testing purposes.


**Description :**

Control flags for NSFDbGetNotes.


**See Also :**
[NSFDbGetNotes](/domino-c-api-docs/reference/Func/NSFDbGetNotes)
---
