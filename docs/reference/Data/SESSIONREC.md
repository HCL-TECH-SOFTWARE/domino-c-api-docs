##### Data Type : Billing
##### SESSIONREC - Session Billing Record
---
```
#include <billing.h>
```

**Definition :**
```
typedef struct {
   SESSIONID SessionID;          
   WORD Action;                  
   char Username[MAXUSERNAME+1]; 
   DWORD BytesIn;              
   DWORD BytesOut;              
   char NetAdr[MAXNETADR];       
} SESSIONREC;
```

**Description :**

To create Session billing records, you must include the Session keyword in the notes.ini BillingClass variable on the billing server. This enables the server to generate billing records related to network activity for each database session on that server.   The billing server writes this information to the billing message queue where it can be read into the SESSREC structure by a billing add-in server task.
<ul><br>
For more information about billing for Domino sessions, see the <i>Administrating the Domino System </i>documentation.<br>
<br>
<b><u>Structure Description</u></b><br>
<br>
<b>SessionID -</b>  Unique identifier (ID) for the user session. <br>
<br>
<b>Action -</b>  State of the session.   There are three types of billing records. <br>
<br>
BILL_SESSION_START -  Written when a user or server initiates database activity for the first time.
<ul><br>
BILL_SESSION_STAMP -  Periodically written for basic session activities, such as opening a database or editing documents in the database.   The frequency of issuance of the stamp is controlled by the BillingSuppressTime variable in the notes.ini file.  The default is 15 minutes.  This record is not written if the session is idle.  <br>
<br>
BILL_SESSION_END -  Written when a workstation or server closes the session.  <br>
</ul>
<b>Username</b> -  Authenticated name of the user for this session.  <b> </b><br>
<br>
<b>BytesIn -</b>  Snapshot of the number of bytes received over the network by the server for the session thus far.  This is a cumulative value that is updated each time a stamp record occurs during the session.  The value is considered final when the server generates the  BILL_SESSION_END record.  The  value includes any client/server network overhead in addition to the session data.<br>
<br>
<b>BytesOut</b> -  Snapshot of the number of bytes sent over the network by the server for the session thus far.  This is a cumulative value that is updated each time a stamp record occurs during the session.  The value is considered final when the server generates the  BILL_SESSION_END record.  The  value includes any client/server network overhead in addition to the session data.<br>
<br>
<b>NetAdr -</b>  Network IP address of the client that initiated the session.<font color="#FF00FF"> </font></ul>



**See Also :**
[AGENTREC](/domino-c-api-docs/reference/Data/AGENTREC)
[BILLMSG](/domino-c-api-docs/reference/Data/BILLMSG)
[BILLREC](/domino-c-api-docs/reference/Data/BILLREC)
[BILL_xxx (actions)](/domino-c-api-docs/reference/Symb/BILL_xxx (actions))
[DBREC](/domino-c-api-docs/reference/Data/DBREC)
[DOCUMENT](/domino-c-api-docs/reference/Data/DOCUMENT)
[HTTPREQREC](/domino-c-api-docs/reference/Data/HTTPREQREC)
[MAILREC](/domino-c-api-docs/reference/Data/MAILREC)
[REPLREC](/domino-c-api-docs/reference/Data/REPLREC)
---
