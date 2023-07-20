##### Symbolic Value : Time
##### TDFMT_xxx - TFMT - Date.  Specifies the Date format for character time/date strings.
---
```
#include <misc.h>
```

**Symbolic Values :**

	TDFMT_FULL	  -  Date format is: year, month, and day

	TDFMT_CPARTIAL	  -  Date format is: month and day, year if not this year

	TDFMT_PARTIAL	  -  Date format is: month and day

	TDFMT_DPARTIAL	  -  Date format is: year and month

	TDFMT_FULL4	  -  Date format is: year (4-digit ), month, and day

	TDFMT_CPARTIAL4	  -  Date format is: month and day, year (4-digit ) if not this year

	TDFMT_DPARTIAL4	  -  Date format is: year (4-digit ) and month


**Description :**

These definitions specify the format for character time/date strings. Use these definitions when you set up the TFMT structure that controls the time/date format.


**See Also :**
[TFMT](/domino-c-api-docs/reference/Data/TFMT)
[ConvertTIMEDATEToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEToText)
[ConvertTIMEDATEPAIRToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEPAIRToText)
[ConvertTextToTIMEDATE](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATE)
[ConvertTextToTIMEDATEPAIR](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATEPAIR)
---
