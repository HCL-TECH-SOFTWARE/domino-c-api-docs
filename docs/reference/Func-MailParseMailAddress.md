##### Function : Mail Gateway
##### MailParseMailAddress - Parses mail originator or recipient address into name and domain.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailParseMailAddress(**

	char far *MailAddress,
	WORD  MailAddressLength,
	char far *UserName,
	WORD  UserNameSize,
	WORD far *UserNameLength,
	char far *DomainName,
	WORD  DomainNameSize,
	WORD far *DomainNameLength);
**Description :**
This function parses a mail originator or recipient address into its user name 
and domain components.  For example, an address of "John Smith @ Iris" will be 
parsed into a user name of "John Smith" and a domain name of "Iris".  Gateways 
should use this funciton to remove the foreign domain name from recipient 
addresses.

The domain name is considered to be the name following the last "@".  For 
example, an address of "Donna Simonides@next.com @ UUCP" will be parsed into a 
user name of "Donna Simonides@next.com" and a domain name of "UUCP".
**Parameters :**
Input :
MailAddress  -  Originator/recipient address string pointer.

MailAddressLength  -  Originator/recipient address string length (not including '\0').

UserNameSize  -  User name string buffer size  (MAXRECIPIENTNAME recommended).

DomainNameSize  -  Domain name string buffer size (MAXDOMAINNAME recommended).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


UserName  -  User name string.

UserNameLength  -  User name string length (not including '\0').

DomainName  -  Domain name string.

DomainNameLength  -  Domain name string length (not including '\0').

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
[MailGetMessageRecipient](D:/md_files/MailGetMessageRecipient.md)
[MailGetMessageOriginator](D:/md_files/MailGetMessageOriginator.md)
---
