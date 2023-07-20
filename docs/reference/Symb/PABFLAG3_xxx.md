##### Symbolic Value : Rich Text
##### PABFLAG3_xxx - Values for DWORD extension to CDPABDEFINITION
---
```
#include <editods.h>
```

**Symbolic Values :**

	PABFLAG3_HIDE_EE	  -  Hide when embedded.

	PABFLAG3_HIDE_MOBILE	  -  Hide from mobile clients.

	PABFLAG3_LAYER_USES_DRM	  -  True if boxes in a layer have set PABFLAG_DISPLAY_RM on pabs.


**Description :**

If the Flags2 member of CDPABDEFINITION is set to PABFLAG2_MORE_FLAGS, the CDPABDEFINITION may be followed by a DWORD extension. If the value of this DWORD extension is EXTENDEDPABFLAGS3, then a second DWORD extension may be present . These DWORD extensions follow the six R5 margin extension WORDs, if they are present.<br>

<ul>If the second DWORD extension is set to PABFLAG3_HIDE_EE, hide when embedded. If it is set to PABFLAG3_HIDE_MOBILE, hide from mobile clients. It is set to PABFLAG3_LAYER_USES_DRM if boxes in a layer have set PABFLAG_DISPLAY_RM for the Flags member of CDPABDEFINITION.</ul>



**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
[EXTENDEDPABFLAGS3](/domino-c-api-docs/reference/Symb/EXTENDEDPABFLAGS3)
---
