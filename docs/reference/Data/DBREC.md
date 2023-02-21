##### Data Type : Billing
##### DBREC - Database Billing Record
---
```
#include <billing.h>
```
**Description :**

To create Database billing records, you must include the Database keyword in 
the notes.ini BillingClass variable on the billing server. This enables the 
server to write database-related information to the billing message queue which 
can then be read into the DBREC structure by a Billing add-in server task.

For more information about billing for database activity, see the Domino 5 
Administration Help database.


Structure Description

SessionID -- Identifier (ID) of the Domino or Notes session established  by the 
Notes workstation or Domino server that initiated the billing activity, such as 
opening a database.

Action --  Type of session activity at the time the billing record occurs.  
Database billing records are written for each of the following activity states:

BILL_DB_STAMP -- Indicates that the database is active with such activities as 
document editing and saving, and access control list updates.  The frequency of 
issuance of this record depends on the BillingSuppressTime notes.ini variable.  
A billing database stamp occurs if the timer specified by BillingSuppresTime 
expires and there is database activity only. The default is 15 minutes. 

BILL_DB_OPEN -- Indicates that the database is open.  Billing records are not 
generated for opening data directories.

BILL_DB_CLOSE - Indicates a user or server request to close the database.  The 
database is not actually closed until the session terminates and a  
BILL_DB_CLOSE_END is issued.  A Lotus Domino Server may not permanently close 
the database until the user session has ended. This can happen when the server 
anticipates heavy usage of a database.  In this way, if a database is opened 
and closed multiple times within a single session, the open time between each 
open/close action can be easily calculated.

BILL_DB_CLOSE_END - Indicates a database is closed at session end.

Username -- Authenticated name of the user who initiated the session.

DBOpenTime -- Elapsed time that a database is open during the session. When a 
database is opened multiple times within a session, a cumulative value is 
recorded for the session.

ReplicaID -- Unique replica ID of the open database.

**See Also :**
[AGENTREC](/domino-c-api-docs/reference/Data/AGENTREC)
[BILLMSG](/domino-c-api-docs/reference/Data/BILLMSG)
[BILLREC](/domino-c-api-docs/reference/Data/BILLREC)
[BILL_xxx (actions)](/domino-c-api-docs/reference/Symb/BILL_xxx (actions))
[DOCUMENT](/domino-c-api-docs/reference/Data/DOCUMENT)
[HTTPREQREC](/domino-c-api-docs/reference/Data/HTTPREQREC)
[MAILREC](/domino-c-api-docs/reference/Data/MAILREC)
[REPLREC](/domino-c-api-docs/reference/Data/REPLREC)
[SESSIONREC](/domino-c-api-docs/reference/Data/SESSIONREC)
---
