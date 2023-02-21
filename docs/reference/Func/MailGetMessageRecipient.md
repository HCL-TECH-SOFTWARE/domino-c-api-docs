##### Function : Mail Gateway
##### MailGetMessageRecipient - Returns recipient address of one of the recipients of a message.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailGetMessageRecipient(

	DARRAY far *MessageList,
	WORD  Message,
	WORD  RecipientNum,
	char far *RecipientName,
	WORD  RecipientNameSize,
	WORD far *RecipientNameLength);
```
**Description :**

This function returns the recipient address of one of the recipients of a 
message.  The address is composed of the foreign user name and foreign domain 
name.  For example, "SYS1.KAWELL @ Profs".

**Parameters :**
Input :
MessageList  -  Message list pointer.

Message  -  Message number (0-n).

RecipientNum  -  Recipient number (0-n).

RecipientNameSize  -  Recipient Address string buffer length.  
(MAXRECIPIENTNAME recommended).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


RecipientName  -  Recipient's address string (null-terminated).

RecipientNameLength  -  Recipient's address string length (not including '\0').


**Sample Usage :**
```
    STATUS      error = NOERROR;
    HANDLE      hMessageList;
    WORD        MessageCount, Msg, RecipientCount, Rec;
    char        RecipientName[MAXRECIPIENTNAME+1];
    WORD        RecipientNameLength;
    char        UserName[MAXUSERNAME + 1];
    WORD        UserNameLength;
    char        DomainName[MAXDOMAINNAME+1];
    WORD        DomainNameLength;


        if (error = MailGetMessageInfo(MessageList, Msg, 
                            &RecipientCount, NULL, NULL))
        {
            printf ("Error: unable to get number of recipients in message.\n");
            MailCloseMessage (hMessage);
            goto Exit2;
        }
        printf ("\tNumber of Recipients = %d.\n", RecipientCount);

        for (Rec = 0; Rec < RecipientCount; Rec++)
        {
            MailGetMessageRecipient(MessageList, Msg, Rec, RecipientName,
                    sizeof(RecipientName), &RecipientNameLength);
            MailParseMailAddress(RecipientName, RecipientNameLength, 
                    UserName, sizeof(UserName), &UserNameLength,
                    DomainName, sizeof(DomainName), &DomainNameLength);

            UserName[UserNameLength] = '\0';
            DomainName[DomainNameLength] = '\0';
            printf ("\t\tRecipient %d = '%s'\t Domain = '%s'\n", Rec,
                                UserName, DomainName);
        }   /* end of loop over recipients */
```
**See Also :**
[MailParseMailAddress](/domino-c-api-docs/reference/Func/MailParseMailAddress)
[MailDeleteMessageRecipient](/domino-c-api-docs/reference/Func/MailDeleteMessageRecipient)
---
