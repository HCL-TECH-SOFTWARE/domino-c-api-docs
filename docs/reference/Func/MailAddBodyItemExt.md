##### Function : Mail Gateway
##### MailAddBodyItemExt - Adds an in-memory text Body item to an open message, allowing use of NLS_INFO structure.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailAddBodyItemExt(

	DHANDLE  hMessage,
	DHANDLE  hBodyItem,
	DWORD  BodyLength,
	NLS_PINFO  pInfo);
```
**Description :**

This function adds an in-memory text Body item to a message, allowing the use 
of the NLS_INFO structure.  Use this function with a text-only body item 
created by MailCreateBodyItem and initialized by MailAppendBodyItemLine.

Use MailAddBodyItem if your program reads text from a file or stream one line 
at a time, and appends the text to a message body. Do not use this function if 
the body will exceed 64K bytes.  For body items larger than 64K, see 
MailAddMessageBodyText.

MailAddBodyItem takes as input a handle to a plain text body item.  First call 
MailCreateBodyItem to create the plain text body item. This yields the body 
item handle, hBodyItem.  Then append one or more lines of text to the body item 
by repeatedly calling MailAppendBodyItemLine. Pass the body item handle as 
input to MailAppendBodyItemLine.  After processing all lines, call 
MailAddBodyItem to add the body to the message. 

MailAddBodyItem converts the plain text specified by hBodyItem into rich text 
and appends the rich text item to the message. After transferring the message 
to the mail box and closing the message, call OSMemFree to free the memory 
associated with the plain text body item handle, hBodyItem.

**Parameters :**
Input :
hMessage  -  Open message handle.

hBodyItem  -  Body item handle.

BodyLength  -  Body length.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().  (NULL if body text already in the Lotus Multibyte Character Set (LMBCS)).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



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

    error = MailAddBodyItemExt(hMessage, hBodyItem, BodySize, NULL);
    if (error) goto Close;

    /* Transfer the message to the local mail router */
Close:
    MailCloseMessage(hMessage);
    OSMemFree(hBodyItem);
    /* close message file */

```
**See Also :**
[MailAddMessageBodyTextExt](/domino-c-api-docs/reference/Func/MailAddMessageBodyTextExt)
[MailAppendBodyItemLine](/domino-c-api-docs/reference/Func/MailAppendBodyItemLine)
[MailCreateBodyItem](/domino-c-api-docs/reference/Func/MailCreateBodyItem)
[OSMemFree](/domino-c-api-docs/reference/Func/OSMemFree)
---
