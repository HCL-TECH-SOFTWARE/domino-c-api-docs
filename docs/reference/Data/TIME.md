##### Data Type : Time
##### TIME - Binary time/date and its integer components.
---
```
#include <misc.h>
```

**Definition :**
```
typedef struct {
   int year;       /* 1-32767 */
   int month;      /* 1-12 */
   int day;        /* 1-31 */
   int weekday;    /* 1-7, Sunday is 1 */
   int hour;       /* 0-23 */
   int minute;     /* 0-59 */
   int second;     /* 0-59 */
   int hundredth;  /* 0-99 */
   int dst;        /* FALSE or TRUE */
   int zone;       /* -11 to +11 */
   TIMEDATE GM;
} TIME;
```

**Description :**

This is the Domino expanded components of a time/date. This structure is used with the TimeGMToLocal and TimeLocalToGM functions.  In addition, the &quot;.GM&quot; member can be altered using any other C API time/date function that manipulates a TIMEDATE structure.


**See Also :**
[OSCurrentTIMEDATE](/domino-c-api-docs/reference/Func/OSCurrentTIMEDATE)
[TimeDateIncrement](/domino-c-api-docs/reference/Func/TimeDateIncrement)
[TimeDateAdjust](/domino-c-api-docs/reference/Func/TimeDateAdjust)
[TimeGMToLocal](/domino-c-api-docs/reference/Func/TimeGMToLocal)
[TimeLocalToGM](/domino-c-api-docs/reference/Func/TimeLocalToGM)
---
