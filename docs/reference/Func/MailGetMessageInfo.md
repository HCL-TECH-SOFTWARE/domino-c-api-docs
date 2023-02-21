##### Function : Mail Gateway
##### MailGetMessageInfo - Returns information about a message in a message list.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailGetMessageInfo(

	DARRAY far *MessageList,
	WORD  Message,
	WORD far *RecipientCount,
	WORD far *Priority,
	WORD far *Report);
```
**Description :**

This function returns information about a message in a message list.

**Parameters :**
Input :
MessageList  -  Message list pointer.

Message  -  Message number (0-n).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


RecipientCount  -  (Optional) - If not NULL, number of recipients in the message.  In Release 4.0 and later, only messages which have been sent have a recipients list.

Priority  -  (Optional) - If not NULL, priority of the message, which can be one of DELIVERY_PRIORITY_xxx.

Report  -  (Optional) - If not NULL, type of delivery reporting requested, which can be one of DELIVERY_REPORT_xxx.


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
[DELIVERY_PRIORITY_xxx](/domino-c-api-docs/reference/Symb/DELIVERY_PRIORITY_xxx)
[DELIVERY_REPORT_xxx](/domino-c-api-docs/reference/Symb/DELIVERY_REPORT_xxx)
[MailGetMessageRecipient](/domino-c-api-docs/reference/Func/MailGetMessageRecipient)
[MailParseMailAddress](/domino-c-api-docs/reference/Func/MailParseMailAddress)
---
