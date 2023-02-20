##### Data Type : Composite Data
##### CDEMBEDDEDCONTACTLIST - Defines properties of an embedded contact list.
---
```
#include <editods.h>
```
**Description :**

This CD record defines properties of an embedded contact list.  The fields in 
this structure are:

Header - Signature and length of this record.
Flags - 
SelectedBackground - Selected background color.  
SelectedText -  
ControlBackground - Control background.
Spare - Reserved for future use - must be zero.  

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.

**See Also :**
[SIG_CD_xxx](/reference/Symb/SIG_CD_xxx)
---
