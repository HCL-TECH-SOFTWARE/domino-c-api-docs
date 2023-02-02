##### Data Type : Billing
##### REPLREC - Replication Billing Record
---
##### #include <billing.h>
**Description :**
To create Replication billing records, you must include the Replication keyword 
in the notes.ini BillingClass variable on the billing server. This enables the 
server to generate billing records for replication activity initiated by that 
server.  This information is written to the billing message queue and can be 
read into the REPLREC structure by a billing add-in server task.

Structure Description

SessionID -  Unique identifier (ID) for the user session.  

BytesIn -  Number of bytes read by the server from the network during 
replication of a database. This value is cumulative. Each database replication 
event updates the value. 

BytesOut -  Number of bytes written by the server to the network during 
replication of a database.  This value is cumulative. Each database replication 
event updates the value. 

ReplicaID -  Replica ID of the database associated with the replication event.

Source -  Name of the server that contains the replicated database.

Destination -  Name of the server that contains the destination replica.    

Priority -  Priority of the replication event, obtained from the connection 
record in the  Domino Directory. The values are Low, Medium, and High.

Notes:
Domino does not generate replication billing records for replications performed 
by the Cluster Replicator.  Only standard Domino replication events generate 
replication billing records.  For more information, see the Administering the 
Domino System documentation.

**See Also :**
[AGENTREC](D:/md_files/AGENTREC.md)
[BILLMSG](D:/md_files/BILLMSG.md)
[BILLREC](D:/md_files/BILLREC.md)
[BILL_xxx (actions)](D:/md_files/BILL_xxx (actions).md)
[DBREC](D:/md_files/DBREC.md)
[DOCUMENT](D:/md_files/DOCUMENT.md)
[HTTPREQREC](D:/md_files/HTTPREQREC.md)
[MAILREC](D:/md_files/MAILREC.md)
[SESSIONREC](D:/md_files/SESSIONREC.md)
---
