##### Data Type : Backup
##### NOTE_RESTORE_CALLBACK_INFO - Note restore callback information structure.
---
```
#include <nsfdb.h>
```

**Definition :**
```
typedef struct {
	WORD  InfoSize; /* Size of this structure, use this to determine 
	       if future fields are avail */ 
	NOTEID  NoteId; /* NoteID for note being altered */
	NOTEHANDLE hNote; /* Handle to note being retrieved */
	TIMEDATE TranTime; /* Time the transaction ran for which you are being 
called */
	char far* UserName; /* If avail, else a pointer to "" */
	char far* PathName; /* Path & file name of DB */
} NOTE_RESTORE_CALLBACK_INFO;
```

**Description :**

Information structure to be used with NOTERESTORECALLBACKFUNCTION.


**See Also :**
[NOTERESTORECALLBACKFUNCTION](/domino-c-api-docs/reference/Data/NOTERESTORECALLBACKFUNCTION)
---
