##### Data Type : Composite Data
##### CDDECSFIELD - Pertains to data connection resource information in a field or form.
---
```
#include <editods.h>
```
**Description :**

This CD Record gives information pertaining to data connection resource 
information in a field or form. The fields in this structure are:

Header - Defines this composite data item as a CDDECSFIELD item.

Flags - see FDECS_xxx 

ExternalNameLength - Length of external field name when external data source is 
used 

MetadataNameLength - Metadata object name length 

DCRNameLength - Data Connection Resource name length 

Spare[8] - Reserved for future use

These fields may be followed by optional items. If you plan to use them, you 
will need to declare the variables and assign values to their lengths.

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note. 

**See Also :**
[FDECS_xxx](/reference/Symb/FDECS_xxx)
---
