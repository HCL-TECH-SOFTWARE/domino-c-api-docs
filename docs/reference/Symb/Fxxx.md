##### Symbolic Value : Form
##### Fxxx - CDFIELD - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	FREADWRITERS	  -  Field contains read/writers

	FEDITABLE	  -  Field is editable, not read only

	FNAMES	  -  Field contains distinguished names

	FSTOREDV	  -  Store Default Value, even if not spec'ed by user

	FREADERS	  -  Field contains document readers

	FSECTION	  -  Field contains a section

	FSPARE3	  -  Can be assumed to be clear in memory (V3 & later)

	FV3FAB	  -  IF CLEAR, CLEAR AS ABOVE

	FCOMPUTED	  -  Field is a computed field

	FKEYWORDS	  -  Field is a keywords field

	FPROTECTED	  -  Field is protected

	FREFERENCE	  -  Field name is simply a reference to a shared field note

	FSIGN	  -  Sign this field during mail signing, or when the field is saved within a section.

	FSEAL	  -  Enable encryption for this field.

	FKEYWORDS_UI_STANDARD	  -  Standard UI

	FKEYWORDS_UI_CHECKBOX	  -  Checkbox UI

	FKEYWORDS_UI_RADIOBUTTON	  -  Radiobutton UI

	FKEYWORDS_UI_ALLOW_NEW	  -  Allow doc editor to add new values.


**Description :**

Defines the flags that may be set in the Flags member of the CDFIELD data structure.


**See Also :**
[CDFIELD](/domino-c-api-docs/reference/Data/CDFIELD)
---
