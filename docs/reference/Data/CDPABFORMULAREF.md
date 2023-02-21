##### Data Type : Composite Data
##### CDPABFORMULAREF - Identify both "Hide When" formula and CDPABDEFINITION record
---
```
#include <editods.h>
```
**Description :**

Starting in Release 4.0 of Notes, a paragraph may have an associated formula 
that determines when the paragraph is to be hidden.  The CDPABFORMULAREF is 
similar to the CDPABREFERENCE record, with an additional field that identifies 
the CDPABDEFINITION record containing the CDPABHIDE record for the "Hide When" 
formula.

The fields in this record are:

Header - Identifies this as a CDPABFORMULAREF record

SourcePABID - ID number of PAB containing the "Hide When" formula

DestPABID - ID number of CDPABDEFINITION record for this paragraph

**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
[CDPABREFERENCE](/domino-c-api-docs/reference/Data/CDPABREFERENCE)
---
