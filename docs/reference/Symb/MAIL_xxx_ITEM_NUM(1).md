##### Symbolic Value : Mail Gateway
##### MAIL_xxx_ITEM_NUM(1) - Mail note item name codes.
---
```
#include <mail.h>
```

**Symbolic Values :**

	MAIL_SENDTO_ITEM_NUM	  -  Message recipient name. Specifies who to send the message to. Use MAIL_SENDTO_LIST_ITEM_NUM if there is more than one recipient. This item is of TYPE_TEXT.

	MAIL_COPYTO_ITEM_NUM	  -  List of recipient names to send copies. This item is of TYPE_TEXT.

	MAIL_FROM_ITEM_NUM	  -  Originator's user name (does not include domain name). This item is of TYPE_TEXT.

	MAIL_SUBJECT_ITEM_NUM	  -  Subject text. This item is of TYPE_TEXT.

	MAIL_COMPOSEDDATE_ITEM_NUM	  -  Date/time message was composed. This item is of TYPE_TIME.

	MAIL_POSTEDDATE_ITEM_NUM	  -  Date/time message was mailed by originator. This item is of TYPE_TIME.

	MAIL_BODY_ITEM_NUM	  -  Body. This item is of TYPE_COMPOSITE.

	MAIL_INTENDEDRECIPIENT_ITEM_NUM	  -  List of intended recipient addresses (Reports only). This item is of TYPE_TEXT.

	MAIL_FAILUREREASON_ITEM_NUM	  -  Failure reason text (Non-Delivery Report only). This item is of TYPE_TEXT.

	MAIL_RECIPIENTS_ITEM_NUM	  -  Message recipient address. Specifies where a saved message was sent. Use MAIL_RECIPIENTS_LIST_ITEM_NUM if there is more than one recipient address. This item is of TYPE_TEXT.

	MAIL_ROUTINGSTATE_ITEM_NUM	  -  Routing state. This item is reserved for the Domino router and should not be used by the gateway. It is of TYPE_TEXT.

	MAIL_FORM_ITEM_NUM	  -  Form name. This item is of TYPE_TEXT.

	MAIL_SAVED_FORM_ITEM_NUM	  -  Original form name (Non-Delivery Report only). This item is of TYPE_TEXT.

	MAIL_BLINDCOPYTO_ITEM_NUM	  -  List of recipient names to send blind copies. This item is of TYPE_TEXT.

	MAIL_DELIVERYPRIORITY_ITEM_NUM	  -  Delivery priority ("H", "N", "L"). This item is of TYPE_TEXT.

	MAIL_DELIVERYREPORT_ITEM_NUM	  -  Delivery report type requested ("N", "B", "C"). This item is of TYPE_TEXT.

	MAIL_DELIVEREDDATE_ITEM_NUM	  -  Date/time message was delivered. This item is of TYPE_TIME.

	MAIL_DELIVERYDATE_ITEM_NUM	  -  Date/time message was delivered (Delivery Reports only). This item is of TYPE_TIME.

	MAIL_CATEGORIES_ITEM_NUM	  -  Categories. This item is of TYPE_TEXT.

	MAIL_FROMDOMAIN_ITEM_NUM	  -  Originator's domain name. This item is of TYPE_TEXT.

	MAIL_SENDTO_LIST_ITEM_NUM	  -  List of message recipient names. Specifies who to send the message to. Used to specify more than one recipient. This item is of TYPE_TEXT_LIST.

	MAIL_RECIPIENTS_LIST_ITEM_NUM	  -  List of message recipient addresses. Specifies where a saved message was sent. Used to specify more than one recipient address. This item is of TYPE_TEXT_LIST.

	MAIL_RECIP_GROUPS_EXP_ITEM_NUM	  -  List of recipient group names that have been expanded. This item is of TYPE_TEXT_LIST.

	MAIL_RETURNRECEIPT_ITEM_NUM	  -  Return receipt requested ("1", "0"). This item is of TYPE_TEXT. Setting this item to "1" means "send a return receipt", setting the item to "0" means "do not send a return receipt."

	MAIL_ROUTE_HOPS_ITEM_NUM	  -  Routing hop count. This item is of TYPE_NUMBER.

	MAIL_CORRELATION_ITEM_NUM	  -  Arbitrary gateway message "correlation" text. This item is used by some gateways to correlate the delivery report with the original message. Any text message may be placed in this item. This item is of TYPE_TEXT.

	MAIL_ORIGINALPATH_ITEM_NUM	  -  Original routing path (copy of original message's FromDomain).

	MAIL_DELIVER_LOOPS_ITEM_NUM	  -  Forwarding loop count.

	MAIL_DEAD_FAILUREREASON_ITEM_NUM	  -  Reason for dead mail failure.


**Description :**

These symbolic constants define the codes (indexes) associated with mail note item names.


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
[MailAddHeaderItem](/domino-c-api-docs/reference/Func/MailAddHeaderItem)
[MailAddHeaderItemByHandle](/domino-c-api-docs/reference/Func/MailAddHeaderItemByHandle)
[MailGetMessageItem](/domino-c-api-docs/reference/Func/MailGetMessageItem)
[MailGetMessageItemHandle](/domino-c-api-docs/reference/Func/MailGetMessageItemHandle)
[MailReplaceHeaderItem](/domino-c-api-docs/reference/Func/MailReplaceHeaderItem)
[MAIL_xxx_ITEM_NUM(2)](/domino-c-api-docs/reference/Symb/MAIL_xxx_ITEM_NUM(2))
---
