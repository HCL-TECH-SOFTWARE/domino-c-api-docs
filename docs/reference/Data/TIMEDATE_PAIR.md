##### Data Type : Time
##### TIMEDATE_PAIR - A range of time in Domino binary format.
---
```
#include <global.h>
```

**Definition :**
```
typedef struct {
   TIMEDATE Lower;
   TIMEDATE Upper;
} TIMEDATE_PAIR;
```

**Description :**

This structure represents a range of time in Domino binary format. The elements of this structure only should be interpreted using the C API time/date calls -- they cannot easily be parsed directly.


**See Also :**
[ConvertTextToTIMEDATEPAIR](/domino-c-api-docs/reference/Func/ConvertTextToTIMEDATEPAIR)
[ConvertTIMEDATEPAIRToText](/domino-c-api-docs/reference/Func/ConvertTIMEDATEPAIRToText)
[OSCurrentTIMEDATE](/domino-c-api-docs/reference/Func/OSCurrentTIMEDATE)
[TYPE_xxx [TIME_RANGE]](/domino-c-api-docs/reference/Symb/TYPE_xxx [TIME_RANGE])
---
