##### Data Type : Billing
##### REPLREC - Replication Billing Record
---
```
#include <billing.h>
```

**Definition :**
```
typedef struct {
   SESSIONID SessionID; 
   DWORD     BytesIn;  
   DWORD     BytesOut;  
   TIMEDATE  ReplicaID;
   char      Source[MAXUSERNAME+1];
   char      Destination[MAXUSERNAME+1];
   WORD      Priority;  
} REPLREC;
```

**Description :**

To create Replication billing records, you must include the Replication keyword in the notes.ini BillingClass variable on the billing server. This enables the server to generate billing records for replication activity initiated by that server.  This information is written to the billing message queue and can be read into the REPLREC structure by a billing add-in server task.
<ul><br>
<br>
<b><u>Structure Description</u></b><br>
<br>
<b>SessionID -</b>  Unique identifier (ID) for the user session. <b> </b><br>
<br>
<b>BytesIn -</b>  Number of bytes read by the server from the network during replication of a database. This value is cumulative. Each database replication event updates the value. <br>
<br>
<b>BytesOut -</b>  Number of bytes written by the server to the network during replication of a database.  This value is cumulative. Each database replication event updates the value. <br>
<br>
<b>ReplicaID -</b>  Replica ID of the database associated with the replication event.<br>
<br>
<b>Source -</b>  Name of the server that contains the replicated database.<br>
<br>
<b>Destination -</b>  Name of the server that contains the destination replica.   <b> </b><br>
<br>
<b>Priority -</b>  Priority of the replication event, obtained from the connection record in the  Domino Directory. The values are Low, Medium, and High.<br>
<br>
<b>Notes:</b><br>
Domino does not generate replication billing records for replications performed by the Cluster Replicator.  Only standard Domino replication events generate replication billing records.  For more information, see the<i> Administering the Domino System </i>documentation.</ul>



**See Also :**
[AGENTREC](/domino-c-api-docs/reference/Data/AGENTREC)
[BILLMSG](/domino-c-api-docs/reference/Data/BILLMSG)
[BILLREC](/domino-c-api-docs/reference/Data/BILLREC)
[BILL_xxx (actions)](/domino-c-api-docs/reference/Symb/BILL_xxx (actions))
[DBREC](/domino-c-api-docs/reference/Data/DBREC)
[DOCUMENT](/domino-c-api-docs/reference/Data/DOCUMENT)
[HTTPREQREC](/domino-c-api-docs/reference/Data/HTTPREQREC)
[MAILREC](/domino-c-api-docs/reference/Data/MAILREC)
[SESSIONREC](/domino-c-api-docs/reference/Data/SESSIONREC)
---
