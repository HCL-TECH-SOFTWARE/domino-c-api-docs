##### Function : Mail Gateway
##### MailOpenMessage - Reads an outbound message from a message list into memory.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailOpenMessage(

	DARRAY far *MessageList,
	WORD  Message,
	DHANDLE far *hMessage);
```
**Description :**

This function opens an outbound message from a message list and reads it into 
memory.  This function is used by gateways to handle messages outbound to a 
foreign mail system.

An open message handle is equivalent to an NSF note handle and can be used, if 
necessary, for direct calls to NSF.  Use MailCloseMessage to close the message 
handle and deallocate the memory associated with it.

**Parameters :**
Input :
MessageList  -  Message list pointer.

Message  -  Message number (0-n).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


hMessage  -  Open message handle


**Sample Usage :**
```
    STATUS      error = NOERROR;
    char       *szServerName;
    char       *szMailFile;
    char        szMailFilePath[MAXPATH+1];
    DHANDLE      hMessageFile;
    DHANDLE      hMessageList = NULLHANDLE, hMessage;
    DARRAY     *MessageList;
    WORD        MessageCount, Msg;

    if (error = MailCreateMessageList(hMessageFile, 
                        &hMessageList, &MessageList, &MessageCount))
    {
        printf ("Error: unable to create message list.\n");
        goto Exit1;
    }

    /* Print out each of the outbound messages. */

    for (Msg = 0; Msg < MessageCount; Msg++)
    {
        printf ("\nMessage #%d: \n", Msg);

        if (error = MailOpenMessage (MessageList, Msg, &hMessage))
        {
            printf ("Error: unable to open message number %d.\n", Msg);
            goto Exit2;
        }
```
**See Also :**
[MailCloseMessage](/domino-c-api-docs/reference/Func/MailCloseMessage)
---
