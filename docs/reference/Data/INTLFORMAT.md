##### Data Type : Time
##### INTLFORMAT - Holds country and workstation settings.
---
```
#include <intl.h>
```
**Description :**

The INTLFORMAT typedef is used to declare a data structure that is returned 
from OSGetIntlSettings with country and workstation dependant information.  
This structure provides information useful in parsing or composing Time, Date, 
and Currency strings.  It is also used by ConvertTextToTIMEDATE and 
ConvertTIMEDATEToText to indicate the expected or resulting string format, 
current time zone and daylight savings values.

Note: The function ConvertTIMEDATEToText does not take the DAYLIGHT_SAVINGS 
flag  into account.

**See Also :**
[CLOCK_24_HOUR](/domino-c-api-docs/reference/Symb/CLOCK_24_HOUR)
[ConvertTextToTIMEDATE](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATE)
[ConvertTIMEDATEToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEToText)
[CURRENCY_SPACE](/domino-c-api-docs/reference/Symb/CURRENCY_SPACE)
[CURRENCY_SUFFIX](/domino-c-api-docs/reference/Symb/CURRENCY_SUFFIX)
[DATE_DMY](/domino-c-api-docs/reference/Symb/DATE_DMY)
[DATE_MDY](/domino-c-api-docs/reference/Symb/DATE_MDY)
[DATE_YMD](/domino-c-api-docs/reference/Symb/DATE_YMD)
[DAYLIGHT_SAVINGS](/domino-c-api-docs/reference/Symb/DAYLIGHT_SAVINGS)
[NUMBER_LEADING_ZERO](/domino-c-api-docs/reference/Symb/NUMBER_LEADING_ZERO)
[OSCurrentTIMEDATE](/domino-c-api-docs/reference/Func/OSCurrentTIMEDATE)
[OSGetIntlSettings](/domino-c-api-docs/reference/Func/OSGetIntlSettings)
---
