##### Function : Mail Gateway
##### MailGetMessageBodyText - Converts message body item(s) to a file of text strings.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailGetMessageBodyText(

	DHANDLE  hMessage,
	char far *ItemName,
	char far *LineDelims,
	WORD  LineLength,
	BOOL  ConvertTabs,
	char far *OutputFileName,
	DWORD far *OutputFileSize);
```
**Description :**

This function returns the message body item(s) and converts them to a file of 
text strings.  This function handles multiple items of the same name and 
therefore is not limited to 64KB of output.

**Parameters :**
Input :
hMessage  -  Open message handle.

ItemName  -  Body item name (null-terminated).  Optional - NULL is "Body".

LineDelims  -  Line delimiter characters (e.g. "\r\n") (null-terminated).  Optional - NULL is "" or null-terminated.

LineLength  -  Line length to wrap lines (usually 80).

ConvertTabs  -  TRUE if TABS are to be converted to spaces.

OutputFileName  -  Output file name (null-terminated).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



OutputFileSize  -  Output file size in bytes.


**Sample Usage :**
```
   if (error = MailGetMessageBodyText(hMessage,
                                NULL,     /* Use standard Body item */
                                "\r\n",    /* Newline-terminate */
                                80,        /* 80 chars per line */
                                TRUE,     /* Convert TABs */
                                BodyFileName,
                                &BodyFileSize))
    {
        printf ("Error: unable to get Message body into temporary file.\n");
        unlink(BodyFileName);
        MailCloseMessage (hMessage);
        goto Exit2;
    }

    /* Print each line of body text to the screen. */

    if (!(BodyFile = fopen(BodyFileName, "r")))
    {
        printf ("Error: unable to open temporary file.\n");
        unlink(BodyFileName);
        MailCloseMessage (hMessage);
        goto Exit2;
    }

    printf ("\tBody:\n");
    while (fgets(String, READMAIL_BODY_LINELEN, BodyFile))
    {
        printf("\t\t%s\n", String);
    }
    fclose(BodyFile);
```
**See Also :**
[MailGetMessageBody](/domino-c-api-docs/reference/Func/MailGetMessageBody)
[MailGetMessageBodyComposite](/domino-c-api-docs/reference/Func/MailGetMessageBodyComposite)
---
