##### Function : Extension Manager
##### SMTPMessageAcceptEMCallback - Extension Manager callback for EM_SMTPMESSAGEACCEPT
---
```
#include <extmgr.h>
STATUS LNPUBLIC SMTPMessageAcceptEMCallback(

	DWORD  SessionID,
	NOTEHANDLE  Note,
	char *SMTPReply,
	DWORD  SMTPReplyLength);
```
**Description :**

EM_SMTPMESSAGEACCEPT is called following the receipt of "end of mail data 
indicator", a line containing a single period, and itemization of the MIME 
stream into an in-memory note.

Following the receipt of the "end of mail data indicator", the resulting stream 
is itemized to an in-memory note.  The Extension Manager EM_BEFORE notification 
type for the EM_SMTPMESSAGEACCEPT event occurs following itemization but prior 
to adding the note to the mailbox.  If the callback routine returns STATUS of 
NOERROR, the Domino SMTP server will stop further processing of the message.  
By default a success response is generated by core Domino code when NOERROR 
STATUS has been returned. It is also possible for the callback routine to 
intercept the message and deposit to database where scans can be performed.  
The Callback routine can make changes to the note in the EM_BEFORE event but 
should not attempt to close the note as this is done by the core code.  

The Extension Manager EM_AFTER notification type for the EM_SMTPMESSAGEACCEPT 
event occurs after the SMTP listener task attempted to submit the message to 
the mailbox but prior to sending a reply.  The Callback routines for the 
EM_AFTER notification can change the reply returned to the connecting host 
however, care must be taken not to change the reply code from success to error 
or vice-versa as this would cause the sender-SMTP and receiver-SMTP servers to 
be out of synch.

**Parameters :**
Input :
SessionID  -  Unique session identifier for the current session.

Note  -  Handle to the note containing the itemized message.

SMTPReplyLength  -  Size of buffer allocated to modify SMTPReply.

Output :
(routine)  -  Return status from the call 
EM_BEFORE event: NOERROR, Domino silently deletes message.  ERR_EM_CONTINUE, Domino accepts message for delivery  Anything else, Domino rejects message.
EM_AFTER event:  Value other than ERR_EM_CONTINUE is ignored.


SMTPReply  -  SMTP Response that will be returned to the connecting host.   EM_BEFORE event: NULL.  EM_AFTER event: NULL terminated string containing RFC821 defined SMTP reply.  


**See Also :**
[EM_xxx](/domino-c-api-docs/reference/Symb/EM_xxx)
---
