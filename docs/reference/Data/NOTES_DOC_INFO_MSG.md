##### Data Type : Notes/FX data
##### NOTES_DOC_INFO_MSG - Notes/FX data sent by Notes to OLE server.
---
```
#include <olenotes.h>
```

**Definition :**
```
typedef struct
	{
	WORD   Version;   /* Version of this structure */
	NOTELINK  DocLink;  /* Document in which OLE object resides */ 
	WORD   DocOpenMode;  /* DOC_OPENMODE_??? flags below */
	WORD   DocFlags;   /* DOC_FLAGS_??? flags below*/
	WORD   UserAccess;     /* USER_ACCESS_??? flags below */
	HWND   hDocWnd;   /* Notes document window handle */
	char   UserName[MAXUSERNAME]; /* Notes user name */
	NOTEHANDLE  hNote;  /* Handle to document's note: THIS IS READ ONLY! 
its lifetime is only for duration of the SetData method */
	NOTEHANDLE  hFXNote;  /* Empty note, associated with document's DB. A 
server should use this for writing items to be applied to hNote */
	WORD    cNumDocActions; /* Count of doc actions, if any. Only passed to 
server if registered to support NotesDocAction GetData() */
	DHANDLE   hDocActions;     /* Notes OSMemAlloc() handle to 
DOC_ACTION_INFO */
	DWORD   dwUnused[2];
	} NOTES_DOC_INFO_MSG;

```

**Description :**

This is the structure of the Notes/FX data sent from Notes to an OLE server's SetData method.  The data in this structure allows data to be exchanged between an OLE object embedded in a note and the note containing the object.


**Sample Usage :**
```
 
```

**See Also :**
[DOC_ACTION_INFO](/domino-c-api-docs/reference/Data/DOC_ACTION_INFO)
[DOC_FLAGS_xxx](/domino-c-api-docs/reference/Symb/DOC_FLAGS_xxx)
[DOC_OPENMODE_xxx](/domino-c-api-docs/reference/Symb/DOC_OPENMODE_xxx)
[NOTES_DOC_INFO_VERSIONxxx](/domino-c-api-docs/reference/Symb/NOTES_DOC_INFO_VERSIONxxx)
[NSFDbReopen](/domino-c-api-docs/reference/Func/NSFDbReopen)
[USER_ACCESS_xxx](/domino-c-api-docs/reference/Symb/USER_ACCESS_xxx)
---
