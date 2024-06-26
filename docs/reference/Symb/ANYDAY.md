##### Symbolic Value : Time
##### ANYDAY - Wildcard value for the Date portion of a TIMEDATE data structure.
---
```
#include <misc.h>
```

**Symbolic Values :**



**Description :**

Wildcard value for the Date portion of a TIMEDATE data structure. Functions that test or compare a TIMEDATE in which the Date portion is set to ANYDAY will succeed for the Date portion of a TIMEDATE. For example: <br>
Suppose you have two TIMEDATES (td1 and td2) that are identical, except td1.Date = ANYDAY and td2.Date = &lt;some valid date&gt;.  If you compare them as follows:<br>
 	td_compare_result = TimeDateCompare(&amp;td1, &amp;td2);<br>
 The integer returned in td_compare_result will be 0, indicating that the two TIMEDATEs are equal.


**See Also :**
[ALLDAY](/domino-c-api-docs/reference/Symb/ALLDAY)
[TIMEDATE](/domino-c-api-docs/reference/Data/TIMEDATE)
---
