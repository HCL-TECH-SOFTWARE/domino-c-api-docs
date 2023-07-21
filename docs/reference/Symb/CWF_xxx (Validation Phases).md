##### Symbolic Value : Note
##### CWF_xxx (Validation Phases) - Validation phases of NSFNoteComputeWithForm.
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	CWF_DV_FORMULA	  -  Error occurred when processing the Default Value formula.

	CWF_IT_FORMULA	  -  Error occurred when processing the Translation formula.

	CWF_IV_FORMULA	  -  Error occurred when processing the Validation formula.

	CWF_COMPUTED_FORMULA	  -  Error occurred when processing the computed field Value formula.

	CWF_DATATYPE_CONVERSION	  -  Error occurred when verifying the data type for the field.

	CWF_COMPUTED_FORMULA_LOAD	  -  Error occurred when processing the computed field Value formula, during the "load" pass.

	CWF_COMPUTED_FORMULA_SAVE	  -  Error occurred when processing the computed field Value formula, during the "save" pass.


**Description :**

The validation phase value is passed to the error callback routine CWF_ERROR_PROC (called by NSFNoteComputeWithForm()).  These values indicate the phase of the validation process where the error was encountered.<br>
<br>
<b>Note:</b><br>
The NSFNoteComputeWithForm API function has a two pass validation process:  The &quot;load&quot; pass runs the default field value and related computed field value formulas. The &quot;save&quot; pass runs the translation, validation, and datatype input field formulas, along with the related computed field value formulas.  Since computed field values are validated for both passes, the error callback function can be called twice for the relevant fields.   Future releases of the Lotus C API for Domino and Notes will expand the validation phases to include the pass that the error occurred in.


**See Also :**
[CWF_ERROR_PROC](/domino-c-api-docs/reference/Data/CWF_ERROR_PROC)
[CWF_xxx (Return Codes)](/domino-c-api-docs/reference/Symb/CWF_xxx (Return Codes))
[NSFNoteComputeWithForm](/domino-c-api-docs/reference/Func/NSFNoteComputeWithForm)
---
