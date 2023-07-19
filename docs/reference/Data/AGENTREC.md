##### Data Type : Billing
##### AGENTREC - Agent Billing Record
---
```
#include <billing.h>
```

**Definition :**

	typedef struct    /*  Agent Billing Record */
 {
    WORD  ULen;   /*  UserName Len */
    WORD  TLen;   /*  TaskName Len */
    WORD  DLen;   /*  DatabaseName Len */
    DWORD  ElapsedRunTime; /*  Elapsed run-time for agent */
    DWORD  Flags;  /*  Agent Flags */
 /* UserName, TaskName, Database Name strings follow */
    } AGENTREC;


**Description :**

To create AGENT billing records you must include the Agent keyword in the notes.ini BillingClass variable on the billing server.  This enables the server to write agent-related information to the billing message queue which can then be read to the AGENTREC structure by the billing server task.
<ul><br>
<br>
For more information about billing for Domino agents, see the<i> Domino 5 Administration Help </i>documentation.<br>
<br>
<b><u>Structure Description</u></b><br>
<br>
<b>ULen</b> -- User name length<br>
<br>
<b>TLen </b>-- Task name length<br>
<br>
<b>DLen</b> -- Database name length<br>
<br>
<b>ElapsedRunTime</b> -- Elapsed runtime for the agent<br>
<br>
<b>Flags</b> -- Agent flags</ul>



**See Also :**
[BILLMSG](/domino-c-api-docs/reference/Data/BILLMSG)
[BILLREC](/domino-c-api-docs/reference/Data/BILLREC)
[BILL_xxx (actions)](/domino-c-api-docs/reference/Symb/BILL_xxx (actions))
[DBREC](/domino-c-api-docs/reference/Data/DBREC)
[DOCUMENT](/domino-c-api-docs/reference/Data/DOCUMENT)
[HTTPREQREC](/domino-c-api-docs/reference/Data/HTTPREQREC)
[MAILREC](/domino-c-api-docs/reference/Data/MAILREC)
[REPLREC](/domino-c-api-docs/reference/Data/REPLREC)
---
