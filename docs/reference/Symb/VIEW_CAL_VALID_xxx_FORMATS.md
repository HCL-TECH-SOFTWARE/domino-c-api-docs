##### Symbolic Value : Calendaring and Scheduling
##### VIEW_CAL_VALID_xxx_FORMATS - Version mask for VIEW_CAL_FORMAT_XXX
---
```
#include <viewfmt.h>
```
**Description :**

This mask indicates the maximum of VIEW_CAL_FORMAT_XXX values specified in the  
VIEW_CALENDAR_FORMAT.Formats item for different versions.

**Sample Usage :**
```
The following code checks the minor version of the calendar format and clear 
out any bit that was not supported prior to verion 5.0.3:


if (CalendarFormat.MinorVersion < VIEW_CAL_FORMAT_MINOR_2)
   CalendarFormat.Formats &= VIEW_CAL_VALID_PRE_503_FORMATS;

```
**See Also :**
[VIEW_CALENDAR_FORMAT](/domino-c-api-docs/reference/Data/VIEW_CALENDAR_FORMAT)
[VIEW_CAL_FORMAT_MINOR_xxx](/domino-c-api-docs/reference/Symb/VIEW_CAL_FORMAT_MINOR_xxx)
[VIEW_CAL_FORMAT_xxx](/domino-c-api-docs/reference/Symb/VIEW_CAL_FORMAT_xxx)
---
