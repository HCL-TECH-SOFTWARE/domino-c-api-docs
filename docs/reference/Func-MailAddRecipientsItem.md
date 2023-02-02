##### Function : Mail Gateway
##### MailAddRecipientsItem - Adds a Recipients item to an open message.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailAddRecipientsItem(**

	DHANDLE  hMessage,
	DHANDLE  hRecipientsItem,
	WORD  RecipientsLength);
**Description :**
This function adds a Recipients item to an open message.  This function is 
usually used by gateways for creating inbound messages from foreign mail 
systems.

The Recipients item consists of a text list of the full mail addresses of all 
the recipients.  The Domino Mail Router requires a Recipients item to deliver 
the message. 

Use the text list manipulation functions (ListAllocate, etc.) to create and 
initialize the recipients item text list.  Use MailLookupAddress to look up the 
full mail address for each recipient, then add each valid address to the list 
before calling MailAddRecipientsItem. The text list item must have a 
TYPE_TEXT_LIST data type prefix word, so specify prefix_flag = TRUE in 
ListAllocate and subsequent List functions.  MailAddRecipientsItem does not 
copy the text list but transfers ownership of the memory associated with the 
text list to the message itself.  Unlock the memory associated with the text 
list but do not free the memory.  The memory will be freed by MailCloseMessage.
**Parameters :**
Input :
hMessage  -  Open message handle.

hRecipientsItem  -  Recipients text list item handle.

RecipientsLength  -  Recipients text list item size.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**Sample Usage :**
```
error = ListAllocate(0, 0, TRUE, &hRecipientsItem, &RecipientsItem, 
                    &RecipientsItemSize);
if (error) goto Close;
OSUnlockObject(hRecipientsItem);

while (fgets(String, sizeof(String), ForeignFile))
{
    Code = String[0];
    Value = &String[1];
    ValueLength = strlen(Value);

    error = ListAddEntry(hRecipientsItem, TRUE, 
            &RecipientsItemSize, Recipients, 
            Value, ValueLength);
}
error = MailAddRecipientsItem(hMessage, hRecipientsItem, RecipientsItemSize);
if (error) goto Close;
hRecipientsItem = NULLHANDLE;
```
**See Also :**
[ListAllocate](D:/md_files/ListAllocate.md)
[ListAddEntry](D:/md_files/ListAddEntry.md)
[MailLookupAddress](D:/md_files/MailLookupAddress.md)
---
