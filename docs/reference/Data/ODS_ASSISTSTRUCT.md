##### Data Type : Agents
##### ODS_ASSISTSTRUCT - Control information for an Agent.
---
```
#include <queryods.h>
```
**Description :**

This record contains the control information for an Agent.  The control 
information specifies what events cause the agent to be run, and what times the 
agent is run.  The fields in this structure are:

wVersion  Version of this structure. Only 0 is currently supported.
wTriggerType  Type of trigger (see ASSISTTRIGGER_TYPE_xxx).
wSearchType  Type of search (see ASSISTSEARCH_TYPE_xxx).
wIntervalType  Type of interval (see ASSISTINTERVAL_TYPE_xxx).
wInterval  Interval;  interpretation depends on the interval type.
dwTime1  Interval time 1;  interpretation depends on the interval type.
dwTime2  Interval time 2;  interpretation depends on the interval type.
StartTime  Agent does not run before this time.
EndTime  Agent does not run after this time.
dwFlags  Flags (see ASSISTODS_FLAG_xxx).
dwSpare  Reserved;  must be 0.

The interval type determines how the wInterval, dwTime1, and dwTime2 fields are 
interpreted;  please see the reference entry for ASSISTINTERVAL_TYPE_xxx for 
details.

**See Also :**
[ASSISTODS_FLAG_xxx](/domino-c-api-docs/reference/Symb/ASSISTODS_FLAG_xxx)
[ASSISTSEARCH_TYPE_xxx](/domino-c-api-docs/reference/Symb/ASSISTSEARCH_TYPE_xxx)
[ASSISTTRIGGER_TYPE_xxx](/domino-c-api-docs/reference/Symb/ASSISTTRIGGER_TYPE_xxx)
[ASSISTINTERVAL_TYPE_xxx](/domino-c-api-docs/reference/Symb/ASSISTINTERVAL_TYPE_xxx)
---
