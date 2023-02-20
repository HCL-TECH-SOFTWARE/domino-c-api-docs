##### Function : Mail Gateway
##### MailTransferMessageLocal - Transfers a message to the local Mail Router.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailTransferMessageLocal(

	DHANDLE  hMessage);
```
**Description :**

This function transfers a message to the local Mail Router by transferring it 
to a mail.box file on the local machine. This function is normally used by mail 
gateway programs running on the Lotus Domino Server.  If there are multiple 
mail.box files on the local machine, this function will transfer the message 
properly.  This function will not succeed on a Notes workstations where there 
is no local mail.box file.

Once a message is transferred to the Router, responsibility for the message is 
also transferred; a gateway does not need to retain any further state regarding 
the message as the Router will either deliver the message or return a 
Non-Delivery Report back to the originator.

**Parameters :**
Input :
hMessage  -  Open message handle.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**Sample Usage :**
```
    /*  Deliver the message. */
    /*  If local, transfer message to the local mail.box */
    if (fLocal)
    {
        if (status = MailTransferMessageLocal(hMsg))
        {
            /* Unable to transfer message to local mail box */
            error = ERR_SENDMAIL_CANTTRANSFER;
            goto CloseMsg;
        }
        /* else we successfully transferred msg to local mail box */
        /* Save msg to user's mail file and clean up.*/
        if (status = NSFNoteUpdate(hMsg, UPDATE_NOCOMMIT))
        {   /* Unable to update message in local mail file */
            error = ERR_SENDMAIL_CANTUPDATEFILE;
        }
        goto CloseMsg;
    }

```
**See Also :**
---
