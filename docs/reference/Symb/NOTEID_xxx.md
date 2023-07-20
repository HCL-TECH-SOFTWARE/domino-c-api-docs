##### Symbolic Value : IDs
##### NOTEID_xxx - Reserved note IDs
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	NOTEID_RESERVED	  -  Reserved note ID used for categories in NIFReadEntries and for deleted notes.

	NOTEID_ADD	  -  Reserved note ID used as input to NoteUpdate, to add a new note (gets error if UNID assigned to new note already exists).

	NOTEID_ADD_OR_REPLACE	  -  Reserved note ID used as input to NoteUpdate, to update if note UNID already exists, or add note if doesn't exist.

	NOTEID_ADD_UNID	  -  Reserved note ID used as input to NoteUpdate. Try to preserve the specified note UNID, but if it already exists, assign a new one. (Note that the UNID in the hNote IS updated.)

	NOTEID_NULL_FOLDER	  -  Reserved note ID used for null folder ids.

	NOTEID_NO_PARENT	  -  Reserved note ID used to indicate that this note has no parent in the response hierarchy.


**Description :**

These symbols indicate special note IDs, such as categories and deleted notes.


**See Also :**
[NOTEID](/domino-c-api-docs/reference/Data/NOTEID)
---
