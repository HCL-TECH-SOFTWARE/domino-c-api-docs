##### Data Type : Time
##### TIMEDATE - Domino binary time/date format.
---
```
#include <global.h>
```
**Description :**

This is the Domino binary time/date format. This structure only should be 
interpreted using the C API time/date calls -- it cannot easily be parsed 
directly.

All TIMEDATEs are stored in GMT. If you need to take a TIMEDATE and store it as 
a GMT time in TIME format, do the following:
- Define a variable of type TIME.
- Copy the TIMEDATE you wish to extract to the .GM member of the TIME structure.
- Set the .zone and .dst members of the TIME structure to zero. This indicates 
that you want the time stored as Greenwich Mean Time, without Daylight Savings 
Time.
- Call the function TimeGMToLocalZone(), passing it a pointer to the TIME 
structure you've defined. This function will fill in the remaining integer 
members of the TIME structure with the time in GMT.

**See Also :**
[ConvertTextToTIMEDATE](/reference/Func/ConvertTextToTIMEDATE)
[ConvertTIMEDATEToText](/reference/Func/ConvertTIMEDATEToText)
[OSCurrentTIMEDATE](/reference/Func/OSCurrentTIMEDATE)
[TimeGMToLocalZone](/reference/Func/TimeGMToLocalZone)
---
