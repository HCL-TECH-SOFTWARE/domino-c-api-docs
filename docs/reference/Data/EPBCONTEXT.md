##### Data Type : Edit Fax
##### EPBCONTEXT - Data structure used by the EditorPrintNoteToBitmap Editfax API.
---
```
#include <editfax.h>
```
**Description :**

This data structure contains the name of the callback routine, and other 
information which are passed to the callback routine by the 
EditorPrintNoteToBitmap Editfax API.


**Sample Usage :**
```
	
EPBCONTEXT EPBContext;
.
.
.

error = EditorPrintNoteToBitmap(hSourceDB,
                                SourceNoteID,
                                &EPBContext);

```
**See Also :**
[EditorPrintNoteToBitmap](/domino-c-api-docs/reference/Func/EditorPrintNoteToBitmap)
[HPAINT](/domino-c-api-docs/reference/Data/HPAINT)
[RECTSIZE](/domino-c-api-docs/reference/Data/RECTSIZE)
---
