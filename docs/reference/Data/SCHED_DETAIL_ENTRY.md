##### Data Type : Calendaring and Scheduling
##### SCHED_DETAIL_ENTRY - Schedule detail list entry.
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
    WORD        wPrefixLen;     /* Length of THIS prefix entry, in case it
                                ** ever grows, so that new items can be 
                                ** easily skipped
                                */
    WORD        wEntryLen;      /* Length of THIS entire entry and ALL of 
                                ** its related data.
                                */
    UNID        Unid;           /* UNID of the entry this is details of */
    WORD        wOffsetDetails; /* Offset from entry start to actual data */
    BYTE        Attr;           /* SCHED_DETAIL_ENTRY_ATTR_xxx attributes (TBD) 
*/
    BYTE        bReserved;      /* Reserved space/padding for ODS */

    /* Now comes the data that corresponds to the item values (1 per item name)
    ** UNLESS dwEntryLen == wPrefixLen (which means NO details available
    ** for this UNID)
    */
} SCHED_DETAIL_ENTRY;
```

**Description :**

Schedule detail list entry.


**See Also :**
[SCHED_DETAIL_DATA](/domino-c-api-docs/reference/Data/SCHED_DETAIL_DATA)
[SCHED_DETAIL_LIST](/domino-c-api-docs/reference/Data/SCHED_DETAIL_LIST)
---
