##### Function : Mail Gateway
##### MailAppendBodyItemLine - Appends a line of text to an in-memory text Body item. 
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailAppendBodyItemLine(

	DHANDLE  hBodyItem,
	DWORD far *BodyLength,
	char far *Text,
	WORD  TextLength);
```
**Description :**

This function appends a line of text to an in-memory text Body item.  Use this 
function in conjunction with MailCreateBodyItem and MailAddBodyItem. 

Do not use MailAppendBodyItemLine if the total size of the message body will 
exceed 64K bytes.  To create larger body items, use MailAddMessageBodyText.

Use MailAppendBodyItemLine if your program reads text from a file or stream one 
line at a time, and appends the text to a message body.  First call 
MailCreateBodyItem to create the body item. This yields the body item handle, 
hBodyItem.  Then append one or more lines of text to the body item by 
repeatedly calling MailAppendBodyItemLine.  Pass the body item handle as input 
to MailAppendBodyItemLine.  After processing all lines, call MailAddBodyItem to 
add the body to the message. 

**Parameters :**
Input :
hBodyItem  -  Body item handle. Obtain this handle by calling MailCreateBodyItem.

BodyLength  -  Body item length pointer.

Text  -  Text line string pointer.

TextLength  -  Text line string length.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


BodyLength  -  Updated body length.


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
[MailCreateBodyItem](/reference/Func/MailCreateBodyItem)
---
