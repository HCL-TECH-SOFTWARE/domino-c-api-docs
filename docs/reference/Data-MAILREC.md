##### Data Type : Billing
##### MAILREC - Mail Billing Record
---
##### #include <billing.h>
**Description :**
To create Mail billing records, you must include the Mail keyword in the 
notes.ini BillingClass variable on the server.  This enables the server to 
generate a Mail billing record for each message that the mail router processes 
which then can be read into the MAILREC structure by a Domino billing add-in 
server task.

For more information about billing for Domino mail activities, see the  Domino 
5 Administration Help database.

Structure Description

FormType:  Type of mail form.  Valid values are part of the C API, in 
stdnames.h, and include MAIL_MEMO_FORM, MAIL_REPLY_FORM, 
MAIL_PHONEMESSAGE_FORM, MAIL_DELIVERYREPORT_FORM, MAIL_NONDELIVERYREPORTFORM, 
MAIL_RETURNRECEIPT_FORM, and MAIL_DATABASEENTRY_FORM.

OriginatorID:  Originator ID (OID) of the mail message, for reporting the 
Universal Note ID (UNID).  The UNID of the mail message uniquely identifies a 
mail message.  However if the message splits due to group expansion, error 
processing, or mail forwarding addressing, a new field ($Orig) is added to the 
note.  The $Orig field contains the original UNID of the mail message.  Since 
mail tries to preserve the UNID of mail messages, the PostedDate value is 
needed to specify a particular instance of a message being sent.

OrigMessageID:  The unique mail identifier (UNID) of the original message.   
This identifier is used to maintain the original message ID when new message 
splits occur.  If NULL, then the OriginatorID value is used to uniquely 
identify a mail message. 

MessageSize:  Total size of the mail message, including header information, 
mail body, and any attachments.

HopName:  Name of the next server to which the mail message is being routed. 
When a message routes through more than one server, this name changes to show 
the next server to receive the message.

Priority:  Delivery priority of the mail message. Values are Low, Normal, and 
High.

Routing State:  See BILL_ROUTINGSTATE_xxx.

Report:  Delivery report request of the mail message.

Originator:  Sender of the mail message as specified in the From: field.

RecipientCount:  Number of intended recipients of the mail message.

RecipientSize:  Size of the recipient list string.

PostedDate:  Date and time when the message was posted to the server mailbox.  
This value, along with the unique message ID, identify the mail billing 
instance.


Notes:

The recipient list string immediately follows the MAILREC structure.  It 
contains a list of recipients, each name delimited by a comma. 

The recipient count is used to determine the number of recipients to which the 
message was delivered.  This allows for crediting of undelivered messages in 
case of delivery errors.
**See Also :**
[AGENTREC](D:/md_files/AGENTREC.md)
[BILLMSG](D:/md_files/BILLMSG.md)
[BILLREC](D:/md_files/BILLREC.md)
[BILL_ROUTINGSTATE_xxx](D:/md_files/BILL_ROUTINGSTATE_xxx.md)
[DBREC](D:/md_files/DBREC.md)
[DOCUMENT](D:/md_files/DOCUMENT.md)
[HTTPREQREC](D:/md_files/HTTPREQREC.md)
[REPLREC](D:/md_files/REPLREC.md)
[SESSIONREC](D:/md_files/SESSIONREC.md)
---
