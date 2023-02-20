##### Symbolic Value : Limits
##### MAXALPHATIMEDATE - The maximum length of a TIMEDATE character string.
---
```
#include <misc.h>
```
**Description :**

This symbol defines the maximum length that a TIMEDATE character string may be. 
By declaring a character array of size MAXALPHATIMEDATE+1, callers of 
ConvertTextToTIMEDATE() or ConvertTIMEDATEToText() are assured that the array 
will be large enough to hold the worst-case (largest) TIMEDATE character 
string.

**See Also :**
[ConvertTextToTIMEDATE](/reference/Func/ConvertTextToTIMEDATE)
[ConvertTIMEDATEToText](/reference/Func/ConvertTIMEDATEToText)
---
