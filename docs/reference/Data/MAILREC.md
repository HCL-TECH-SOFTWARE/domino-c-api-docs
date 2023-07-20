##### Data Type : Billing
##### MAILREC - Mail Billing Record
---
```
#include <billing.h>
```

**Definition :**
```
typedef struct {
   char     FormType[DESIGN_NAME_MAX]; /* Type of Form */ 
   OID      OriginatorID;              /* Message Id */
   UNID     OrigMessageID;             /* $Ref if NonDelivery
                                          Report */
   DWORD    MessageSize;               /* Size of message */
   char     HopName[MAXUSERNAME+1];    /* Next Server Name */
   WORD     Priority;                  /* Delivery priority */
   WORD     RoutingState;              /* see 
                                          BILL_ROUTINGSTATE_xxx */
   WORD     Report;                    /* Delivery report
                                          request */
   char     Originator[MAXUSERNAME+1]; /* From: */
   WORD     RecipientCount;            /* Recipients count */
   WORD     RecipientSize;             /* Recipients string size */
   TIMEDATE PostedDate;                /* Uniquely identify
                                          instance of Mail
                                          message */
/* Recipients char string immediately follows this structure */
} MAILREC;
```

**Description :**

To create Mail billing records, you must include the Mail keyword in the notes.ini BillingClass variable on the server.  This enables the server to generate a Mail billing record for each message that the mail router processes which then can be read into the MAILREC structure by a Domino billing add-in server task.
<ul><br>
<br>
For more information about billing for Domino mail activities, see the <i> </i><i>Domino 5 Administration Help</i> database<i>.</i><br>
<br>
<b><u>Structure Description</u></b><br>
<br>
<b>FormType</b>:  Type of mail form.  Valid values are part of the C API, in stdnames.h, and include MAIL_MEMO_FORM, MAIL_REPLY_FORM, MAIL_PHONEMESSAGE_FORM, MAIL_DELIVERYREPORT_FORM, MAIL_NONDELIVERYREPORTFORM, MAIL_RETURNRECEIPT_FORM, and MAIL_DATABASEENTRY_FORM.<br>
<br>
<b>OriginatorID</b>:  Originator ID (OID) of the mail message, for reporting the Universal Note ID (UNID).  The UNID of the mail message uniquely identifies a mail message.  However if the message splits due to group expansion, error processing, or mail forwarding addressing, a new field ($Orig) is added to the note.  The $Orig field contains the original UNID of the mail message.  Since mail tries to preserve the UNID of mail messages, the PostedDate value is needed to specify a particular instance of a message being sent.<br>
<br>
<b>OrigMessageID</b>:  The unique mail identifier (UNID) of the original message.   This identifier is used to maintain the original message ID when new message splits occur.  If NULL, then the OriginatorID value is used to uniquely identify a mail message. <br>
<br>
<b>MessageSize</b>:  Total size of the mail message, including header information, mail body, and any attachments.<br>
<br>
<b>HopName</b>:  Name of the next server to which the mail message is being routed. When a message routes through more than one server, this name changes to show the next server to receive the message.<br>
<br>
<b>Priority</b>:  Delivery priority of the mail message. Values are Low, Normal, and High.<br>
<br>
<b>Routing State</b>:  See BILL_ROUTINGSTATE_xxx.<br>
<br>
<b>Report</b>:  Delivery report request of the mail message.<br>
<br>
<b>Originator</b>:  Sender of the mail message as specified in the From: field.<br>
<br>
<b>RecipientCount</b>:  Number of intended recipients of the mail message.<br>
<br>
<b>RecipientSize</b>:  Size of the recipient list string.<br>
<br>
<b>PostedDate</b>:  Date and time when the message was posted to the server mailbox.  This value, along with the unique message ID, identify the mail billing instance.<br>
<br>
<br>
<b><u>Notes</u></b><b>:</b><br>
<br>
The recipient list string immediately follows the MAILREC structure.  It contains a list of recipients, each name delimited by a comma. <br>
<br>
The recipient count is used to determine the number of recipients to which the message was delivered.  This allows for crediting of undelivered messages in case of delivery errors.</ul>



**See Also :**
[AGENTREC](/domino-c-api-docs/reference/Data/AGENTREC)
[BILLMSG](/domino-c-api-docs/reference/Data/BILLMSG)
[BILLREC](/domino-c-api-docs/reference/Data/BILLREC)
[BILL_ROUTINGSTATE_xxx](/domino-c-api-docs/reference/Symb/BILL_ROUTINGSTATE_xxx)
[DBREC](/domino-c-api-docs/reference/Data/DBREC)
[DOCUMENT](/domino-c-api-docs/reference/Data/DOCUMENT)
[HTTPREQREC](/domino-c-api-docs/reference/Data/HTTPREQREC)
[REPLREC](/domino-c-api-docs/reference/Data/REPLREC)
[SESSIONREC](/domino-c-api-docs/reference/Data/SESSIONREC)
---
