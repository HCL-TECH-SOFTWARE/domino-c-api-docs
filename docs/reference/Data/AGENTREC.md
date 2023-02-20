##### Data Type : Billing
##### AGENTREC - Agent Billing Record
---
```
#include <billing.h>
```
**Description :**

To create AGENT billing records you must include the Agent keyword in the 
notes.ini BillingClass variable on the billing server.  This enables the server 
to write agent-related information to the billing message queue which can then 
be read to the AGENTREC structure by the billing server task.

For more information about billing for Domino agents, see the Domino 5 
Administration Help documentation.

Structure Description

ULen -- User name length

TLen -- Task name length

DLen -- Database name length

ElapsedRunTime -- Elapsed runtime for the agent

Flags -- Agent flags

**See Also :**
[BILLMSG](/reference/Data/BILLMSG)
[BILLREC](/reference/Data/BILLREC)
[BILL_xxx (actions)](/reference/Symb/BILL_xxx (actions))
[DBREC](/reference/Data/DBREC)
[DOCUMENT](/reference/Data/DOCUMENT)
[HTTPREQREC](/reference/Data/HTTPREQREC)
[MAILREC](/reference/Data/MAILREC)
[REPLREC](/reference/Data/REPLREC)
---
