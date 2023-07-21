##### Symbolic Value : Note
##### CWF_xxx (Return Codes) - Return codes for callback routine called by NSFNoteComputeWithForm().
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	CWF_ABORT	  -  End all processing by NSFNoteComputeWithForm() and return the error status to the caller.

	CWF_NEXT_FIELD	  -  End validation of the current field and go on to the next.

	CWF_RECHECK_FIELD	  -  Begin the validation process for this field over again.


**Description :**

These are the values that may be returned from the callback function CWF_ERROR_PROC (called from NSFNoteComputeWithForm()).  The value returned will determine the subsequent processing.


**See Also :**
[CWF_ERROR_PROC](/domino-c-api-docs/reference/Data/CWF_ERROR_PROC)
[CWF_xxx (Validation Phases)](/domino-c-api-docs/reference/Symb/CWF_xxx (Validation Phases))
[NSFNoteComputeWithForm](/domino-c-api-docs/reference/Func/NSFNoteComputeWithForm)
---
