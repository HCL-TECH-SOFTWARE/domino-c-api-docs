##### Data Type : Composite Data
##### CDTABLEDATAEXTENSION - Specifies extended table properties.
---
```
#include <editods.h>
```
**Description :**

This record was added because the Pre Table Begin Record can not be expanded 
and R6 required more data to be stored.

This CD record specifies extended table properties. It is preceded by 
CDPRETABLEBEGIN. Both records may be encapsulated within a CDBEGINRECORD and 
CDENDRECORD. 

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.

These fields may be followed by optional items. If you plan to use them, you 
will need to declare the variables and assign values to their lengths.

**See Also :**
[CDPRETABLEBEGIN](/domino-c-api-docs/reference/Data/CDPRETABLEBEGIN)
---
