##### Data Type : Composite Data
##### CDDECSFIELD - Pertains to data connection resource information in a field or form.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
 WSIG Header;
 WORD Flags;
 WORD ExternalNameLength;
 WORD MetadataNameLength;
 WORD DCRNameLength;
 WORD Spare[8];
} CDDECSFIELD;


**Description :**

This CD Record gives information pertaining to data connection resource information in a field or form. The fields in this structure are:<br>

<ul><br>
Header - Defines this composite data item as a CDDECSFIELD item.<br>
<br>
Flags - see FDECS_xxx <br>
<br>
ExternalNameLength - Length of external field name when external data source is used <br>
<br>
MetadataNameLength - Metadata object name length <br>
<br>
DCRNameLength - Data Connection Resource name length <br>
<br>
Spare[8] - Reserved for future use<br>
<br>
These fields may be followed by optional items. If you plan to use them, you will need to declare the variables and assign values to their lengths.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note. </ul>



**See Also :**
[FDECS_xxx](/domino-c-api-docs/reference/Symb/FDECS_xxx)
---
