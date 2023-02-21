##### Data Type : Composite Data
##### CDBOXSIZE - Defines size information for a layer box. 
---
```
#include <editods.h>
```
**Description :**

This CD record contains size information for a layer box. The units (pixels, 
twips, etc.) for the Width and Height are set in the "Units" members of the 
"Top", "Left", "Bottom" and "Right" members of the CDPOSITIONING structure. The 
fields in this record are:

Header  Signature and Length of this CD record.
Width  The width of the box.   
Height  The height of the box.   
Reserved Reserved for future use.  
dwReserved Reserved for future use.

**See Also :**
[CDLAYER](/domino-c-api-docs/reference/Data/CDLAYER)
[CDPOSITIONING](/domino-c-api-docs/reference/Data/CDPOSITIONING)
---
