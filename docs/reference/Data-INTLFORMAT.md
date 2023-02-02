##### Data Type : Time
##### INTLFORMAT - Holds country and workstation settings.
---
##### #include <intl.h>
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
[CLOCK_24_HOUR](D:/md_files/CLOCK_24_HOUR.md)
[ConvertTextToTIMEDATE](D:/md_files/ConvertTextToTIMEDATE.md)
[ConvertTIMEDATEToText](D:/md_files/ConvertTIMEDATEToText.md)
[CURRENCY_SPACE](D:/md_files/CURRENCY_SPACE.md)
[CURRENCY_SUFFIX](D:/md_files/CURRENCY_SUFFIX.md)
[DATE_DMY](D:/md_files/DATE_DMY.md)
[DATE_MDY](D:/md_files/DATE_MDY.md)
[DATE_YMD](D:/md_files/DATE_YMD.md)
[DAYLIGHT_SAVINGS](D:/md_files/DAYLIGHT_SAVINGS.md)
[NUMBER_LEADING_ZERO](D:/md_files/NUMBER_LEADING_ZERO.md)
[OSCurrentTIMEDATE](D:/md_files/OSCurrentTIMEDATE.md)
[OSGetIntlSettings](D:/md_files/OSGetIntlSettings.md)
---
