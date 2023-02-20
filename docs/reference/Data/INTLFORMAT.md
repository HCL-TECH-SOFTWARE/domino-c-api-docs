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
[CLOCK_24_HOUR](/reference/Symb/CLOCK_24_HOUR)
[ConvertTextToTIMEDATE](/reference/Func/ConvertTextToTIMEDATE)
[ConvertTIMEDATEToText](/reference/Func/ConvertTIMEDATEToText)
[CURRENCY_SPACE](/reference/Symb/CURRENCY_SPACE)
[CURRENCY_SUFFIX](/reference/Symb/CURRENCY_SUFFIX)
[DATE_DMY](/reference/Symb/DATE_DMY)
[DATE_MDY](/reference/Symb/DATE_MDY)
[DATE_YMD](/reference/Symb/DATE_YMD)
[DAYLIGHT_SAVINGS](/reference/Symb/DAYLIGHT_SAVINGS)
[NUMBER_LEADING_ZERO](/reference/Symb/NUMBER_LEADING_ZERO)
[OSCurrentTIMEDATE](/reference/Func/OSCurrentTIMEDATE)
[OSGetIntlSettings](/reference/Func/OSGetIntlSettings)
---
