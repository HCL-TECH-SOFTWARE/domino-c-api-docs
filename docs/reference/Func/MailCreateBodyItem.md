##### Function : Mail Gateway
##### MailCreateBodyItem - Creates an empty in-memory text Body item.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailCreateBodyItem(

	DHANDLE far *rethBodyItem,
	DWORD far *retBodyLength);
```
**Description :**

Creates an empty in-memory text Body item. Use this function to create 
text-only message body items.  Do not use this function if the body will exceed 
64K bytes.  To create larger body items, use MailAddMessageBodyText.

Use MailCreateBodyItem if your program reads text from a file or stream one 
line at a time, and appends the text to a message body. First call 
MailCreateBodyItem to create the body item.  This yields the body item handle, 
rethBodyItem. Then append one or more lines of text to the body item by 
repeatedly calling MailAppendBodyItemLine. Pass the body item handle as input 
to MailAppendBodyItemLine.  After processing all lines, call MailAddBodyItem to 
add the body to the message. 

After transferring the message to the mail box and closing the message, call 
OSMemFree to free the memory associated with the body item handle, 
rethBodyItem.

**Parameters :**

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


rethBodyItem  -  Body item handle.

retBodyLength  -  Body item length (initial allocation).


**Sample Usage :**
```

    STATUS error; 
    DHANDLE hMailboxFile, hMessage, hBodyItem;
    DWORD BodySize;
    char String[MAXFILELINELEN];

    /* Call MailOpenMessgeFile- this initializes hMailBoxFile */
    /* Call MailCreateMessage - this initializes hMessage */
    /* Open text input file */

    error = MailCreateBodyItem(&hBodyItem, &BodySize);
    if (error) goto done;

    while (/* still more text in input file /))
    {
        /* get next line from input file into String[] */

        error = MailAppendBodyItemLine(hBodyItem, &BodySize, String, 
strlen(String));
        if (error) break;
    }

    /* close text input file */

    error = MailAddBodyItem(hMessage, hBodyItem, BodySize, NULL);
    if (error) goto Close;

    /* Transfer the message to the local mail router */
Close:
    MailCloseMessage(hMessage);
    OSMemFree(hBodyItem);
    /* close message file */
```
**See Also :**
[MailAddBodyItemExt](/reference/Func/MailAddBodyItemExt)
[MailAddMessageBodyTextExt](/reference/Func/MailAddMessageBodyTextExt)
[MailAppendBodyItemLine](/reference/Func/MailAppendBodyItemLine)
[OSMemFree](/reference/Func/OSMemFree)
---
