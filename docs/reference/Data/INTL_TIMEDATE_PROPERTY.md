##### Data Type : Time
##### INTL_TIMEDATE_PROPERTY - Property values to set for converting an extended International TIMEDATE value.
---
```
#include <misc.h>
```

**Definition :**

typedef enum
{
	AMStringProperty = 1,  
	PMStringProperty = 2
} INTL_TIMEDATE_PROPERTY;

**Description :**

Either an AMStringProperty value or a PMStringProperty value can be set using the function IntlTIMEDATESetValue(..)


**See Also :**
[IntlTIMEDATEConvertToText](/domino-c-api-docs/reference/Func/IntlTIMEDATEConvertToText)
[IntlTIMEDATEGetValue](/domino-c-api-docs/reference/Func/IntlTIMEDATEGetValue)
[IntlTIMEDATESetValue](/domino-c-api-docs/reference/Func/IntlTIMEDATESetValue)
---
