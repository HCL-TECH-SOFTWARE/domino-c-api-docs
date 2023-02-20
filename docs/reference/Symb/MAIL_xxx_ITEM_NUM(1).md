##### Symbolic Value : Mail Gateway
##### MAIL_xxx_ITEM_NUM(1) - Mail note item name codes.
---
```
#include <mail.h>
```
**Description :**

These symbolic constants define the codes (indexes) associated with mail note 
item names.

**Sample Usage :**
```
    /* SendTo */
    MailGetMessageItem (hMessage, MAIL_SENDTO_ITEM_NUM, String, 
                                    MAXSPRINTF, &StringLength);

    String[StringLength] = '\0';
    printf ("\tTo: %s\n", String);

    /* CopyTo */
    MailGetMessageItem (hMessage, MAIL_COPYTO_ITEM_NUM, String, 
                                        MAXSPRINTF, &StringLength);
    String[StringLength] = '\0';
    printf ("\tCc: %s\n", String);

    /* From */
    MailGetMessageItem (hMessage, MAIL_FROM_ITEM_NUM, String, 
                                      MAXSPRINTF, &StringLength);
    String[StringLength] = '\0';
    printf ("\tFrom: %s\n", String);
```
**See Also :**
[MailAddHeaderItem](/reference/Func/MailAddHeaderItem)
[MailAddHeaderItemByHandle](/reference/Func/MailAddHeaderItemByHandle)
[MailGetMessageItem](/reference/Func/MailGetMessageItem)
[MailGetMessageItemHandle](/reference/Func/MailGetMessageItemHandle)
[MailReplaceHeaderItem](/reference/Func/MailReplaceHeaderItem)
[MAIL_xxx_ITEM_NUM(2)](/reference/Symb/MAIL_xxx_ITEM_NUM(2))
---
