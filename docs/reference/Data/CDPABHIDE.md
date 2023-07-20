##### Data Type : Composite Data
##### CDPABHIDE - "Hide When" formula for a paragraph.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;
   WORD PABID;
   BYTE Reserved[8];
} CDPABHIDE;
```

**Description :**

This record contains the &quot;Hide When&quot; formula for a paragraph attributes block.  The fields in this structure are:
<ul><br>

<ul>Header	Identifies this as a CDPABHIDE record.<br>
<br>
PABID		ID number of the PAB this formula applies to.</ul>
<br>
This record is followed by the actual formula.</ul>



**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
---
