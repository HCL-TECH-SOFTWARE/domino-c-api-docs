##### Data Type : Composite Data
##### CDTABLEEND - Specifies the end of a table.
---
```
#include <editods.h>
```
**Description :**

This structure specifies the end of a table. Use this structure when accessing 
a table in a rich text field.

Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.

**See Also :**
[CDTABLEBEGIN](/reference/Data/CDTABLEBEGIN)
[CDTABLECELL](/reference/Data/CDTABLECELL)
[ODSReadMemory](/reference/Func/ODSReadMemory)
[ODSWriteMemory](/reference/Func/ODSWriteMemory)
---