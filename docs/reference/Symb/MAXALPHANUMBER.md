##### Symbolic Value : Limits
##### MAXALPHANUMBER - The maximum length of a NUMBER that can be represented as a character string.
---
```
#include <misc.h>
```
**Description :**

This symbol defines the maximum length of a character string that represents a 
number.  By declaring a character array of size MAXALPHANUMBER, callers of 
ConvertTextToFLOAT() or ConvertFLOATToText() are assured that the array will be 
large enough to hold the worst-case (largest) NUMBER character string.

**See Also :**
[ConvertFLOATToText](/reference/Func/ConvertFLOATToText)
[ConvertTextToFLOAT](/reference/Func/ConvertTextToFLOAT)
---
