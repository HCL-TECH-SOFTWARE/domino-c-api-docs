##### Data Type : Calendaring and Scheduling
##### SCHED_DETAIL_DATA - Schedule detail list actual data.
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {

    WORD        wType;          /* Notes data type for the data */
    WORD        wDataLen;       /* Length of the data that immediately follows 
*/
    BYTE        Attr;           /* SCHED_DETAIL_DATA_ATTR_xxx attributes */
    BYTE        bReserved;      /* Reserved space/padding for ODS */

    /* Now comes the actual data that corresponds to the item values */
} SCHED_DETAIL_DATA;
```

**Description :**

Schedule detail list actual data.


**See Also :**
[SCHED_DETAIL_ENTRY](/domino-c-api-docs/reference/Data/SCHED_DETAIL_ENTRY)
[SCHED_DETAIL_LIST](/domino-c-api-docs/reference/Data/SCHED_DETAIL_LIST)
---
