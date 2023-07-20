##### Symbolic Value : Note
##### CWF_xxx (Flags) - NSFNoteComputeWithForm validation flag - dwFlags
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	CWF_CONTINUE_ON_ERROR	  -  Ignore error processing for fields.


**Description :**

If CWF_CONTINUE_ON_ERROR is specified in the dwFlags argument of the NSFNoteComputeWithForm function, then error processing is ignored for the fields will be skipped and the error callback function will not be called.


**See Also :**
[CWF_ERROR_PROC](/domino-c-api-docs/reference/Data/CWF_ERROR_PROC)
[NSFNoteComputeWithForm](/domino-c-api-docs/reference/Func/NSFNoteComputeWithForm)
---
