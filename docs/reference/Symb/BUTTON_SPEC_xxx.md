##### Symbolic Value : Composite Data
##### BUTTON_SPEC_xxx - CDDATAFLAGS - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	BUTTON_SPEC_NORMAL	  -  Button with this attribute is normal.

	BUTTON_SPEC_DEFAULT	  -  Button with this attribute is the default push button in a dialog box.

	BUTTON_SPEC_MASK	  -  BUTTON_SPEC_DEFAULT


**Description :**

On-disk flags for CDDATAFLAGS. For buttons with type information, the CDBUTTON record is followed by a CDDATAFLAGS structure with its Flags member set to a BUTTON_TYPE_xxx value. If the button type is the default type, the Flags member is set to the BUTTON_SPEC_DEFAULT value.


**See Also :**
---
