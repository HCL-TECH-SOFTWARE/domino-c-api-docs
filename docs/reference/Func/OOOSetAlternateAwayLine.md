##### Function : OOO
##### OOOSetAlternateAwayLine - This function sets the value the alternate first line.
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOSetAlternateAwayLine(

	OOOCTXPTR *pOOOContext,
	char *altline);
```

**Description :**

This function sets the value the alternate first line, replacing the standard  &quot;I am out of the office starting &lt;date&gt; returning &lt;date&gt;&quot;.  <br>
This line will be used for one out of office session.  If it is not set during the next enablement, the old standard message will be used. <br>
This function should be called AFTER OOOSetAwayPeriod.


**Parameters :**
Input :
pOOOContext  -  obtained from the OOOStartOperation call.

altline  -  buffer holding string to set.

Output :
(routine)  -  NOERROR - Successfully performed this operation
This function can return Domino errors.
OOO specific errors:
ERR_OOO_MISSING_PARAM - One or more mandatory parameters were not specified.




**See Also :**
[OOOGetAwayPeriod](/domino-c-api-docs/reference/Func/OOOGetAwayPeriod)
---
