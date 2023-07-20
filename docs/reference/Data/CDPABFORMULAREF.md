##### Data Type : Composite Data
##### CDPABFORMULAREF - Identify both "Hide When" formula and CDPABDEFINITION record
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
 BSIG Header;
 WORD SourcePABID; /* ID number of the source PAB
                           containing the formula. */
 WORD DestPABID;   /* ID number of the dest PAB */
} CDPABFORMULAREF;
```

**Description :**

Starting in Release 4.0 of Notes, a paragraph may have an associated formula that determines when the paragraph is to be hidden.  The CDPABFORMULAREF is similar to the CDPABREFERENCE record, with an additional field that identifies the CDPABDEFINITION record containing the CDPABHIDE record for the &quot;Hide When&quot; formula.
<ul><br>
<br>
The fields in this record are:<br>
<br>
Header - Identifies this as a CDPABFORMULAREF record<br>
<br>
SourcePABID - ID number of PAB containing the &quot;Hide When&quot; formula<br>
<br>
DestPABID - ID number of CDPABDEFINITION record for this paragraph</ul>



**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
[CDPABREFERENCE](/domino-c-api-docs/reference/Data/CDPABREFERENCE)
---
