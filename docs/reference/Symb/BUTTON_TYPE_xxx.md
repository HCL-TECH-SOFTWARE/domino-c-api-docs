##### Symbolic Value : Composite Data
##### BUTTON_TYPE_xxx - CDDATAFLAGS - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	BUTTON_TYPE_NORMAL	  -  button type is normal

	BUTTON_TYPE_OK	  -  button type is ok

	BUTTON_TYPE_CANCEL	  -  button type is cancel

	BUTTON_TYPE_HELP	  -  button type is help

	BUTTON_TYPE_MASK	  -  BUTTON_TYPE_OK | BUTTON_TYPE_CANCEL | BUTTON_TYPE_HELP


**Description :**

On-disk flags for CDDATAFLAGS. For buttons with type information, the CDBUTTON record is followed by a CDDATAFLAGS structure with its Flags member set to a BUTTON_TYPE_xxx value.


**See Also :**
[CDDATAFLAGS](/domino-c-api-docs/reference/Data/CDDATAFLAGS)
---
