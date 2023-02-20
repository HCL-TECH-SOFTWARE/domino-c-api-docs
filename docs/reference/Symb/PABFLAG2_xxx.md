##### Symbolic Value : Rich Text
##### PABFLAG2_xxx - CDPABDEFINITION - Flags2
---
```
#include <editdflt.h>
```
**Description :**

Possible optional values for the Flags2 member of the CDPABDEFINITION 
structure.  These symbols specify additional paragraph attribute flags.  If the 
Flags2 member of CDPABDEFINITION is set to PABFLAG2_MORE_FLAGS, the 
CDPABDEFINITION may be followed by a DWORD extension. If the value of this 
DWORD extension is EXTENDEDPABFLAGS3, then a second DWORD extension may be 
present with a value of PABFLAG3_HIDE_EE. These DWORD extensions follow the six 
R5 margin extension WORDs, if they are present.

**See Also :**
[CDPABDEFINITION](/reference/Data/CDPABDEFINITION)
[EXTENDEDPABFLAGS3](/reference/Symb/EXTENDEDPABFLAGS3)
---
