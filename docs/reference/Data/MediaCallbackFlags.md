##### Data Type : Backup
##### MediaCallbackFlags - Media callback flags.
---
```
#include <nsfdb.h>
```
**Description :**

Values from this enumeration type are returned by NOTESRESTORECALLBACKFUNCTION 
to indicate the type of action performed on a particular note during media 
recovery.  The action types are:

MediaCallback_NoteUpdate - Update of existing note.

MediaCallback_NoteInsert - Addition of new note.

MediaCallback_NoteDelete - Deletion of note.

MediaCallback_CLR - Event is the undo of an action due to some failure.

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
