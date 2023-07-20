##### Symbolic Value : Mail Gateway
##### MAIL_xxx_ITEM_NUM(2) - Mail note item name codes.
---
```
#include <mail.h>
```

**Symbolic Values :**

	MAIL_SMTPORIGINATOR_ITEM_NUM	  -  SMTP Originator

	MAIL_INETTO_ITEM_NUM	  -  List of internet recipient names to send the message to.

	MAIL_INETCC_ITEM_NUM	  -  List of internet recipient names to send copies to.

	MAIL_INETBCC_ITEM_NUM	  -  List of internet recipient names to send blind copies to.

	MAIL_ALTTO_ITEM_NUM	  -  List of alternate recipient names to send the message to.

	MAIL_ALTCC_ITEM_NUM	  -  List of alternate recipient names to send copies to.

	MAIL_ALTBCC_ITEM_NUM	  -  List of alternate recipient names to send blind copies to.

	MAIL_DONOTHOLD_ITEM_NUM	  -  Do not hold this message.

	MAIL_STORAGETO_ITEM_NUM	  -  Storage type for INETTO.

	MAIL_STORAGECC_ITEM_NUM	  -  Storage type for INETCC.

	MAIL_STORAGEBCC_ITEM_NUM	  -  Storage type for INETBCC.

	MAIL_LANGTO_ITEM_NUM	  -  Language tag for INETTO

	MAIL_LANGCC_ITEM_NUM	  -  Language tag for INETCC

	MAIL_LANGBCC_ITEM_NUM	  -  Language tag for INETBCC

	MAIL_INETFROM_ITEM_NUM	  -  Internet originator.

	MAIL_SMTP_DSN_RCPTS_ITEM_NUM	  -  SMTP Delivery Status Notification Receipts.

	MAIL_JOURNAL_FLAG_ITEM_NUM	  -  $JournalResponsibility flag.


**Description :**

These symbolic constants define additional codes (indexes) associated with mail note item names.


**See Also :**
[MailAddHeaderItem](/domino-c-api-docs/reference/Func/MailAddHeaderItem)
[MailAddHeaderItemByHandle](/domino-c-api-docs/reference/Func/MailAddHeaderItemByHandle)
[MailGetMessageItem](/domino-c-api-docs/reference/Func/MailGetMessageItem)
[MailGetMessageItemHandle](/domino-c-api-docs/reference/Func/MailGetMessageItemHandle)
[MailReplaceHeaderItem](/domino-c-api-docs/reference/Func/MailReplaceHeaderItem)
[MAIL_xxx_ITEM_NUM(1)](/domino-c-api-docs/reference/Symb/MAIL_xxx_ITEM_NUM(1))
---
