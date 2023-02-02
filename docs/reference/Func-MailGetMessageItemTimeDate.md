##### Function : Mail Gateway
##### MailGetMessageItemTimeDate - Returns the value of a time/date header item.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailGetMessageItemTimeDate(**

	DHANDLE  hMessage,
	WORD  ItemCode,
	TIMEDATE far *retTimeDate);
**Description :**
This function returns the value of a time/date header item.
**Parameters :**
Input :
hMessage  -  Open message handle.

ItemCode  -  Item code:  MAIL_COMPOSEDDATE_ITEM_NUM, MAIL_DELIVEREDDATE_ITEM_NUM, MAIL_DELIVERYDATE_ITEM_NUM, MAIL_POSTEDDATE_ITEM_NUM

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


retTimeDate  -  Time/date.

**Sample Usage :**
```
        /* PostedDate */
        MailGetMessageItemTimeDate(hMessage, MAIL_POSTEDDATE_ITEM_NUM, &Time);
        ConvertTIMEDATEToText(NULL, NULL, &Time, String, 
                                    sizeof(String), &StringLength);
        String[StringLength] = '\0';
        printf("\tDate: %s\n", String);

```
**See Also :**
[MAIL_xxx_ITEM_NUM(1)](D:/md_files/MAIL_xxx_ITEM_NUM(1).md)
---
