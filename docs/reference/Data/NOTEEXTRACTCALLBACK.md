##### Data Type : File Attachment
##### NOTEEXTRACTCALLBACK - Note extract function
---
```
#include <nsfnote.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR NOTEEXTRACTCALLBACK)(const BYTE *bytes, DWORD 
length, void far *pParam);
```

**Description :**

This is the datatype of the Action routine passed to NSFNoteExtractWithCallback.


**See Also :**
[NSFNoteExtractWithCallback](/domino-c-api-docs/reference/Func/NSFNoteExtractWithCallback)
---
