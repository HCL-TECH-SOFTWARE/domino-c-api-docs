##### Symbolic Value : Note
##### CWF_xxx (Validation Phases) - Validation phases of NSFNoteComputeWithForm.
---
```
#include <nsfnote.h>
```
**Description :**

The validation phase value is passed to the error callback routine 
CWF_ERROR_PROC (called by NSFNoteComputeWithForm()).  These values indicate the 
phase of the validation process where the error was encountered.

Note:
The NSFNoteComputeWithForm API function has a two pass validation process:  The 
"load" pass runs the default field value and related computed field value 
formulas. The "save" pass runs the translation, validation, and datatype input 
field formulas, along with the related computed field value formulas.  Since 
computed field values are validated for both passes, the error callback 
function can be called twice for the relevant fields.   Future releases of the 
Lotus C API for Domino and Notes will expand the validation phases to include 
the pass that the error occurred in.

**See Also :**
[CWF_ERROR_PROC](/reference/Data/CWF_ERROR_PROC)
[CWF_xxx (Return Codes)](/reference/Symb/CWF_xxx (Return Codes))
[NSFNoteComputeWithForm](/reference/Func/NSFNoteComputeWithForm)
---
