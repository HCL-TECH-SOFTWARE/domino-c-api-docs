##### Data Type : Calendaring and Scheduling
##### SCHMSG - Scheduling Request/Reply message structure
---
```
#include <schgtw.h>
```

**Definition :**
```
typedef struct { 
   DWORD    dwFlags;         /* Flags (see SCHMSG_xxx) */
   WORD     wFunction;       /* function name (see SCHFUNC_RQST_xxx) */
   HCNTNR   hMsgCntnr;       /* handle to a container object */
   STATUS   error;
   TIMEDATE tdRequestQueued; /* time request was queued */
   DWORD    spare[5];
} SCHMSG;
```

**Description :**

Used by gateways to pass in scheduling requests.


**See Also :**
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[SCHMSG_xxx](/domino-c-api-docs/reference/Symb/SCHMSG_xxx)
[SCHFUNC_RQST_xxx](/domino-c-api-docs/reference/Symb/SCHFUNC_RQST_xxx)
---
