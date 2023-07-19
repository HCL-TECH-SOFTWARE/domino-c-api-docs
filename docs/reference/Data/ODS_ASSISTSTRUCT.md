##### Data Type : Agents
##### ODS_ASSISTSTRUCT - Control information for an Agent.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WORD     wVersion;      /* Structure version */
   WORD     wTriggerType;  /* Type of trigger */
   WORD     wSearchType;   /* Type of search */
   WORD     wIntervalType; /* Type of interval */
   WORD     wInterval;     /* Interval */
   DWORD    dwTime1;       /* depends on interval type */
   DWORD    dwTime2;       /* depends on interval type */
   TIMEDATE StartTime;     /* Agent does not run before this time */
   TIMEDATE EndTime;       /* Agent does not run after this time */
   DWORD    dwFlags;
   DWORD    dwSpare[16];
} ODS_ASSISTSTRUCT;

**Description :**

This record contains the control information for an Agent.  The control information specifies what events cause the agent to be run, and what times the agent is run.  The fields in this structure are:
<ul><br>

<ul>wVersion		Version of this structure. Only 0 is currently supported.<br>
wTriggerType		Type of trigger (see ASSISTTRIGGER_TYPE_xxx).<br>
wSearchType		Type of search (see ASSISTSEARCH_TYPE_xxx).<br>
wIntervalType		Type of interval (see ASSISTINTERVAL_TYPE_xxx).<br>
wInterval		Interval;  interpretation depends on the interval type.<br>
dwTime1		Interval time 1;  interpretation depends on the interval type.<br>
dwTime2		Interval time 2;  interpretation depends on the interval type.<br>
StartTime		Agent does not run before this time.<br>
EndTime		Agent does not run after this time.<br>
dwFlags		Flags (see ASSISTODS_FLAG_xxx).<br>
dwSpare		Reserved;  must be 0.<br>
</ul>
The interval type determines how the wInterval, dwTime1, and dwTime2 fields are interpreted;  please see the reference entry for ASSISTINTERVAL_TYPE_xxx for details.</ul>



**See Also :**
[ASSISTODS_FLAG_xxx](/domino-c-api-docs/reference/Symb/ASSISTODS_FLAG_xxx)
[ASSISTSEARCH_TYPE_xxx](/domino-c-api-docs/reference/Symb/ASSISTSEARCH_TYPE_xxx)
[ASSISTTRIGGER_TYPE_xxx](/domino-c-api-docs/reference/Symb/ASSISTTRIGGER_TYPE_xxx)
[ASSISTINTERVAL_TYPE_xxx](/domino-c-api-docs/reference/Symb/ASSISTINTERVAL_TYPE_xxx)
---
