##### Function : Mail Gateway
##### MailCreateMessageList - Scans a message file and creates an in-memory message list.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailCreateMessageList(**

	DBHANDLE  hFile,
	DHANDLE far *hMessageList,
	DARRAY far * far *MessageList,
	WORD far *MessageCount);
**Description :**
This function scans a message file and creates an in-memory list of the 
messages in the file.

The summary information for each message includes a list of all recipients for 
each message.  If all the messages in the file cannot be included in the 
message list (currently limited to 64KB), only the messages that will fit will 
be included.  It is assumed that the gateway will transfer the included 
messages and periodically call this function to get any new messages and any 
messages that could not be processed the first time.  (In practice, overflowing 
64KB appears to rarely happen.)

  Use MailFreeMessageList to deallocate the memory used for storing the message 
list.
**Parameters :**
Input :
hFile  -  Open message file handle.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


hMessageList  -  Handle to the in-memory message list.

MessageList  -  Pointer to the in-memory message list.

MessageCount  -  Number of messages in the message list.

**Sample Usage :**
```
    char       *szMailFile;
    char        szMailFilePath[MAXPATH+1];
    DHANDLE      hMessageFile;
    DHANDLE      hMessageList = NULLHANDLE;
    DARRAY     *MessageList;
    WORD        MessageCount;
   
   
    /* Open the message file. */

    if (error = MailOpenMessageFile(szMailFilePath, &hMessageFile))
    {
        printf ("Error: unable to open '%s'.\n", szMailFilePath);
        goto Exit0;
    }

    /* Create message list of messages in the file - just 64K */

    if (error = MailCreateMessageList(hMessageFile, 
                        &hMessageList, &MessageList, &MessageCount))
    {
        printf ("Error: unable to create message list.\n");
        goto Exit1;
    }

    printf ("There are %d messages in the message file.\n", MessageCount);
```
**See Also :**
[MailOpenMessageFile](D:/md_files/MailOpenMessageFile.md)
[MailOpenMessage](D:/md_files/MailOpenMessage.md)
[MailFreeMessageList](D:/md_files/MailFreeMessageList.md)
---
