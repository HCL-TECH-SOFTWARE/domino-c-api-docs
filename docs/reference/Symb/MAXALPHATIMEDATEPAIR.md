##### Symbolic Value : Limits
##### MAXALPHATIMEDATEPAIR - The maximum length of a TIMEDATE_PAIR character string.
---
```
#include <misc.h>
```

**Symbolic Values :**



**Description :**

This symbol defines the maximum length that a TIMEDATE_PAIR character string may be. By declaring a character array of size MAXALPHATIMEDATEPAIR +1, callers of ConvertTextToTIMEDATEPAIR() or ConvertTIMEDATEPAIRToText() are assured that the array will be large enough to hold the worst-case (largest) TIMEDATE_PAIR character string.<br>

<ul>MAXALPHATIMEDATEPAIR is defined as (MAXALPHATIMEDATE *2 + 3).  This includes three characters for the space dash space separator(&quot; - &quot;).</ul>



**See Also :**
[ConvertTextToTIMEDATEPAIR](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATEPAIR)
[ConvertTIMEDATEPAIRToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEPAIRToText)
---
