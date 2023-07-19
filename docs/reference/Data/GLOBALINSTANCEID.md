##### Data Type : IDs
##### GLOBALINSTANCEID - Globally identifies an instance of a note.
---
```
#include <nsfdata.h>
```

**Definition :**

typedef struct {
   DBID     File;   /* database Creation time/date */
   TIMEDATE Note;   /* note Modification time/date */
   NOTEID   NoteID; /* note ID within database */
} GLOBALINSTANCEID;

**Description :**

This structure globally identifies an instance of a note across databases. If we are doing a SEARCH_ALL_VERSIONS, the note with the latest modification date is the one that is the &quot;most recent&quot; instance.


**See Also :**
[NSFNoteGetInfo](/domino-c-api-docs/reference/Func/NSFNoteGetInfo)
---
