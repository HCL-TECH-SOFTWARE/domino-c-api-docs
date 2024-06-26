##### Symbolic Value : Time
##### TZFMT_xxx - TFMT - Zone.  Specifies the Time Zone format for character time/date strings.
---
```
#include <misc.h>
```

**Symbolic Values :**

	TZFMT_NEVER	  -  All times converted to this time zone

	TZFMT_SOMETIMES	  -  Show only when outside this time zone

	TZFMT_ALWAYS	  -  Show time zone on all times, regardless


**Description :**

These definitions specify the format for character time/date strings. Use these definitions when you set up the TFMT structure that controls the time/date format.


**See Also :**
[CDEXT2FIELD](/domino-c-api-docs/reference/Data/CDEXT2FIELD)
[ConvertTextToTIMEDATE](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATE)
[ConvertTextToTIMEDATEPAIR](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATEPAIR)
[ConvertTIMEDATEPAIRToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEPAIRToText)
[ConvertTIMEDATEToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEToText)
[TFMT](/domino-c-api-docs/reference/Data/TFMT)
---
