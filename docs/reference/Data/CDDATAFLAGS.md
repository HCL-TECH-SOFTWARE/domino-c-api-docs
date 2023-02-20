##### Data Type : Composite Data
##### CDDATAFLAGS - Collapsible section, button type, style sheet or field limit information for Notes/Domino 6.
---
```
#include <editods.h>
```
**Description :**

Contains collapsible section, button type, style sheet or field limit 
information for Notes/Domino 6. A CD record (CDBAR, CDBUTTON, CDBORDERINFO, 
CDFIELDHINT, etc.) may be followed by a CDDATAFLAGS structure. 

The fields in this structure are:

Header - Defines this composite data item as a CDDATAFLAGS item.

nFlags - Number of flags.  

elemType - CD_SECTION_ELEMENT, CD_BUTTONEX_ELEMENT or CD_FIELDLIMIT_ELEMENT

dwReserved - Future use.

If the value of the nFlags member is greater than zero, then immediately 
following this structure there will be n DWORD Flags that identify the value of 
the Flags data border, button type, style sheet or field limit.  You can use 
the macros GETDATABORDERTYPE and SETDATABORDERTYPE to get and set each of the 
Flags.

   If elemType is CD_FIELDLIMIT_ELEMENT, you can use Flag & 
FIELD_LIMIT_TYPE_XXX is not zero to get the limit type.  See 
FIELD_LIMIT_TYPE_XXX.

Note that CDDATAFLAGS records reside in items of type TYPE_COMPOSITE. 
Therefore, API programs that run on non-Intel architecture platforms must 
perform host/canonical conversion on structures of this type when accessing 
these records in an item in a note.

**See Also :**
[BARREC_DATA_BORDER_xxx](/reference/Symb/BARREC_DATA_BORDER_xxx)
[BUTTON_TYPE_xxx](/reference/Symb/BUTTON_TYPE_xxx)
[CDBAR](/reference/Data/CDBAR)
[CDBUTTON](/reference/Data/CDBUTTON)
[CDFIELDHINT](/reference/Data/CDFIELDHINT)
[CD_xxx_ELEMENT](/reference/Symb/CD_xxx_ELEMENT)
[GETDATABORDERTYPE](/reference/Func/GETDATABORDERTYPE)
[SETDATABORDERTYPE](/reference/Func/SETDATABORDERTYPE)
[SIG_CD_xxx](/reference/Symb/SIG_CD_xxx)
---
