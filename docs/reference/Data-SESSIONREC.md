##### Data Type : Billing
##### SESSIONREC - Session Billing Record
---
##### #include <billing.h>
**Description :**
To create Session billing records, you must include the Session keyword in the 
notes.ini BillingClass variable on the billing server. This enables the server 
to generate billing records related to network activity for each database 
session on that server.   The billing server writes this information to the 
billing message queue where it can be read into the SESSREC structure by a 
billing add-in server task.
For more information about billing for Domino sessions, see the Administrating 
the Domino System documentation.

Structure Description

SessionID -  Unique identifier (ID) for the user session. 

Action -  State of the session.   There are three types of billing records. 

BILL_SESSION_START -  Written when a user or server initiates database activity 
for the first time.

BILL_SESSION_STAMP -  Periodically written for basic session activities, such 
as opening a database or editing documents in the database.   The frequency of 
issuance of the stamp is controlled by the BillingSuppressTime variable in the 
notes.ini file.  The default is 15 minutes.  This record is not written if the 
session is idle.  

BILL_SESSION_END -  Written when a workstation or server closes the session.  

Username -  Authenticated name of the user for this session.   

BytesIn -  Snapshot of the number of bytes received over the network by the 
server for the session thus far.  This is a cumulative value that is updated 
each time a stamp record occurs during the session.  The value is considered 
final when the server generates the  BILL_SESSION_END record.  The  value 
includes any client/server network overhead in addition to the session data.

BytesOut -  Snapshot of the number of bytes sent over the network by the server 
for the session thus far.  This is a cumulative value that is updated each time 
a stamp record occurs during the session.  The value is considered final when 
the server generates the  BILL_SESSION_END record.  The  value includes any 
client/server network overhead in addition to the session data.

NetAdr -  Network IP address of the client that initiated the session. 
**See Also :**
[AGENTREC](D:/md_files/AGENTREC.md)
[BILLMSG](D:/md_files/BILLMSG.md)
[BILLREC](D:/md_files/BILLREC.md)
[BILL_xxx (actions)](D:/md_files/BILL_xxx (actions).md)
[DBREC](D:/md_files/DBREC.md)
[DOCUMENT](D:/md_files/DOCUMENT.md)
[HTTPREQREC](D:/md_files/HTTPREQREC.md)
[MAILREC](D:/md_files/MAILREC.md)
[REPLREC](D:/md_files/REPLREC.md)
---
