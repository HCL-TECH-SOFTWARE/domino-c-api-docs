##### Symbolic Value : Time
##### ANYDAY - Wildcard value for the Date portion of a TIMEDATE data structure.
---
```
#include <misc.h>
```
**Description :**

Wildcard value for the Date portion of a TIMEDATE data structure. Functions 
that test or compare a TIMEDATE in which the Date portion is set to ANYDAY will 
succeed for the Date portion of a TIMEDATE. For example: 
Suppose you have two TIMEDATES (td1 and td2) that are identical, except 
td1.Date = ANYDAY and td2.Date = <some valid date>.  If you compare them as 
follows:
  td_compare_result = TimeDateCompare(&td1, &td2);
 The integer returned in td_compare_result will be 0, indicating that the two 
TIMEDATEs are equal.

**See Also :**
[ALLDAY](/reference/Symb/ALLDAY)
[TIMEDATE](/reference/Data/TIMEDATE)
---
