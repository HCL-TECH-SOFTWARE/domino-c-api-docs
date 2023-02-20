##### Symbolic Value : Rich Text
##### PABFLAG3_xxx - Values for DWORD extension to CDPABDEFINITION
---
```
#include <editods.h>
```
**Description :**

If the Flags2 member of CDPABDEFINITION is set to PABFLAG2_MORE_FLAGS, the 
CDPABDEFINITION may be followed by a DWORD extension. If the value of this 
DWORD extension is EXTENDEDPABFLAGS3, then a second DWORD extension may be 
present . These DWORD extensions follow the six R5 margin extension WORDs, if 
they are present.

If the second DWORD extension is set to PABFLAG3_HIDE_EE, hide when embedded. 
If it is set to PABFLAG3_HIDE_MOBILE, hide from mobile clients. It is set to 
PABFLAG3_LAYER_USES_DRM if boxes in a layer have set PABFLAG_DISPLAY_RM for the 
Flags member of CDPABDEFINITION.

**See Also :**
[CDPABDEFINITION](/reference/Data/CDPABDEFINITION)
[EXTENDEDPABFLAGS3](/reference/Symb/EXTENDEDPABFLAGS3)
---
