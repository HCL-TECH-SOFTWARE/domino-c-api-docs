##### Data Type : Backup
##### MediaCallbackFlags - Media callback flags.
---
```
#include <nsfdb.h>
```

**Definition :**

typedef enum {
	MediaCallback_NoteUpdate = 0x01, /* Update of existing Note */
	MediaCallback_NoteInsert = 0x02, /* Addition of new note */
	MediaCallback_NoteDelete = 0x04, /* Delete of note */
	MediaCallback_CLR        = 0x08 /* Event is the undo of an action due 
to some failure */
} MediaCallbackFlags;

**Description :**

Values from this enumeration type are returned by NOTESRESTORECALLBACKFUNCTION to indicate the type of action performed on a particular note during media recovery.  The action types are:
<ul>
<ul><br>
MediaCallback_NoteUpdate - Update of existing note.<br>
<br>
MediaCallback_NoteInsert - Addition of new note.<br>
<br>
MediaCallback_NoteDelete - Deletion of note.<br>
<br>
MediaCallback_CLR - Event is the undo of an action due to some failure.</ul>
</ul>



**Sample Usage :**
```
switch (state_flags)
{
	case MediaCallback_NoteInsert:
	  strcpy(note_action, "Addition");
	  break;

	case MediaCallback_NoteDelete:
	  strcpy(note_action, "Deletion");
	  break;

	case MediaCallback_CLR:
	  strcpy(note_action, "Undo");
	  break;

	default:
	  strcpy(note_action, "Unknown");
}
```

**See Also :**
[NOTERESTORECALLBACKFUNCTION](/domino-c-api-docs/reference/Data/NOTERESTORECALLBACKFUNCTION)
[NSFRecoverDatabasesWithCallback](/domino-c-api-docs/reference/Func/NSFRecoverDatabasesWithCallback)
---
