##### Data Type : Edit Fax
##### EPBPROC - Definition of the callback routine for the Editfax API EditorPrintNoteToBitmap.
---
```
#include <editfax.h>
```

**Definition :**
```
typedef BOOL (FAR PASCAL * EPBPROC)(
   void *EPBContext,
   WORD PageNumber);
```

**Description :**

The EditorPrintNoteToBitmap Editfax API calls this user-implemented callback routine for each page in a specified note.  PageNumber is a 1-based page number. 


**See Also :**
[EditorPrintNoteToBitmap](/domino-c-api-docs/reference/Func/EditorPrintNoteToBitmap)
---
