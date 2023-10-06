##### Function : OOO
##### OOOGetAlternateAwayLine - This function returns the value the alternate first line.
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOGetAlternateAwayLine(

	OOOCTXPTR *pOOOContext,
	char *altline,
	WORD  altlinelen);
```

**Description :**

This function returns the value the alternate first line, replacing the standard &quot;I am out of the office starting &lt;date&gt; returning &lt;date&gt;&quot;. <br>
This line will be used for one out of office session. If it is not set during the next enablement, the standard message will be used.<br>
This function returns the value of the alternate first line only if the dates indicate that the value was set during the current OOO session. <br>
In other words this means this function should be called AFTER OOOSetAwayPeriod and OOOSetAlternateAwayLine was executed.


**Parameters :**
Input :
pOOOContext  -  obtained from the OOOStartOperation call.

altlinelen  -  buffer size of altline holding the result string.

Output :
(routine)  -  NOERROR - Successfully performed this operation
This function can return Domino errors.
OOO specific errors:
ERR_OOO_MISSING_PARAM - One or more mandatory parameters were not specified.


altline  -  buffer holding the return string, end by '\0'.



**See Also :**
[OOOGetAwayPeriod](/domino-c-api-docs/reference/Func/OOOGetAwayPeriod)
---
