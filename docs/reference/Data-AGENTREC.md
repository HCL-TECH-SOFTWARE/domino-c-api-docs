##### Data Type : Billing
##### AGENTREC - Agent Billing Record
---
##### #include <billing.h>
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
[BILLMSG](D:/md_files/BILLMSG.md)
[BILLREC](D:/md_files/BILLREC.md)
[BILL_xxx (actions)](D:/md_files/BILL_xxx (actions).md)
[DBREC](D:/md_files/DBREC.md)
[DOCUMENT](D:/md_files/DOCUMENT.md)
[HTTPREQREC](D:/md_files/HTTPREQREC.md)
[MAILREC](D:/md_files/MAILREC.md)
[REPLREC](D:/md_files/REPLREC.md)
---
