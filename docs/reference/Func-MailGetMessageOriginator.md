##### Function : Mail Gateway
##### MailGetMessageOriginator - Returns name/address of the originator of a message.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailGetMessageOriginator(**

	DARRAY far *MessageList,
	WORD  Message,
	char far *OriginatorName,
	WORD  OriginatorNameSize,
	WORD far *OriginatorNameLength);
**Description :**
This function returns the name/address of the originator of a message.  The 
originator of a message is the user name and domain name of the sender of a 
message.
**Parameters :**
Input :
MessageList  -  Message list pointer.

Message  -  Message number (0-n).

OriginatorNameSize  -  Originator string buffer size.  (MAXRECIPIENTNAME recommended).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


OriginatorName  -  Originator name/address string (null-terminated).

OriginatorNameLength  -  Originator string length (not including '\0').

**Sample Usage :**
```
    DARRAY     *MessageList;
    WORD        MessageCount, Msg;;
    char        Originator[MAXRECIPIENTNAME+1];
    WORD        OriginatorLength;


        if (error = MailGetMessageOriginator(MessageList, Msg, 
                Originator, sizeof(Originator), &OriginatorLength))
        {
            printf ("Error: unable to get message originator.\n");
            goto Exit2;
        }

        Originator[OriginatorLength] = '\0';

        printf ("\tOriginator = '%s'\n", Originator);
```
**See Also :**
[MailGetMessageOriginatorDomain](D:/md_files/MailGetMessageOriginatorDomain.md)
---
