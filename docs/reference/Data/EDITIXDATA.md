##### Data Type : Add-In DLL
##### EDITIXDATA - Contains import/export information.
---
```
#include <addinmen.h>
```
**Description :**

This structure provides import/export data as well as the name of the field and 
type of field of the current cursor position.  Menu add-in functions receive 
this information when processing the NAMM_COMMAND message from Notes.

The CaretFieldName member of the EDITIXDATA structure gives the name of the 
field containing the cursor when the menu item was chosen.  The CaretFieldType 
member of the EDITIXDATA structure gives the field type of the field containing 
the cursor when the Notes user selected the menu add-in's item from the Tools 
menu.  See FIELD_TYPE_xxx for the values for CaretFieldType.

**See Also :**
[NAM_CONTEXT_DATA](/reference/Data/NAM_CONTEXT_DATA)
[EDITIMPORTDATA](/reference/Data/EDITIMPORTDATA)
[EDITEXPORTDATA](/reference/Data/EDITEXPORTDATA)
[FIELD_TYPE_xxx](/reference/Symb/FIELD_TYPE_xxx)
---
