##### Function : Mail Gateway
##### MailAddHeaderItemByHandle - Adds a header item to an open message.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailAddHeaderItemByHandle(

	DHANDLE  hMessage,
	WORD  ItemCode,
	DHANDLE  hValue,
	WORD  ValueLength,
	WORD  ItemFlags);
```
**Description :**

This function adds a header item to an open message.  Use this function to add 
items if your program has a handle to the item value. If your program has a 
pointer to the item value, use MailAddHeaderItem.

Unlock the handle to the item value before calling this function. This function 
transfers the memory specified by the handle to the message. If the function 
returns successfully, do not free this memory.

Use MailAddHeaderItemByHandle if your program has a handle to the item value, 
particularly text lists created with ListAllocate. Use ListAllocate and 
ListAddEntry to initialize the list. Unlock but do not free the list. Add the 
list to the message by calling MailAddHeaderItemByHandle. 
MailAddHeaderItemByHandle adds the list to the message efficiently because it 
transfers ownership of the memory specified by the handle to the message. It 
does not allocate additional memory for the item value, nor does it copy the 
item value. Therefore, if MailAddHeaderItemByHandle succeeds, do not free the 
memory specified by the handle.

This function always sets the ITEM_SUMMARY item flag, allowing the item to be 
used in views and formulas.  However, if the value length is greater than 8KB, 
NSF clears the ITEM_SUMMARY flag.

**Parameters :**
Input :
hMessage  -  Open message handle.

ItemCode  -  Item code; all of the MAIL_xxx_ITEM_NUM item codes are valid.

hValue  -  Item value handle.

ValueLength  -  Item value length.

ItemFlags  -  Optional NSF item flags (ITEM_SIGN, ITEM_SEAL).

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**Sample Usage :**
```

    if (error = ListAllocate(0, 0, TRUE, &hToItem, &ToItem, &ToItemSize))
    {
        goto Close;
    }
    OSUnlockObject(hToItem);

    for (/* each SendTo name */)
    {
        error = ListAddEntry(hToItem, TRUE, &ToItemSize, ToEntries, Value, 
ValueLength);
        ToEntries++;
    }
  
    if (error = MailAddHeaderItemByHandle(hMessage, MAIL_SENDTO_ITEM_NUM, 
hToItem, ToItemSize, 0))
    {
        goto Close;
    }
    hToItem = NULLHANDLE;

```
**See Also :**
[ListAddEntry](/domino-c-api-docs/reference/Func/ListAddEntry)
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[MailAddHeaderItem](/domino-c-api-docs/reference/Func/MailAddHeaderItem)
[MAIL_xxx_ITEM_NUM(1)](/domino-c-api-docs/reference/Symb/MAIL_xxx_ITEM_NUM(1))
[MAIL_xxx_ITEM_NUM(2)](/domino-c-api-docs/reference/Symb/MAIL_xxx_ITEM_NUM(2))
---
