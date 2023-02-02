##### Function : Mail Gateway
##### MailAddHeaderItem - Adds a header item to an open message.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailAddHeaderItem(**

	DHANDLE  hMessage,
	WORD  ItemCode,
	const void far *Value,
	WORD  ValueLength);
**Description :**
This function adds a header item to an open message.  The item is added by 
passing a pointer to the item value.

This function always sets the ITEM_SUMMARY item flag, allowing the item to be 
used in views and formulas.  However, if the item value is greater than 8KB, 
NSF clears the ITEM_SUMMARY flag.
**Parameters :**
Input :
hMessage  -  Open message handle.

ItemCode  -  Item code; all of the MAIL_xxx_ITEM_NUM item codes are valid.

Value  -  Item value pointer.

ValueLength  -  Item value length.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**See Also :**
[MailAddHeaderItemByHandle](D:/md_files/MailAddHeaderItemByHandle.md)
[MAIL_xxx_ITEM_NUM(1)](D:/md_files/MAIL_xxx_ITEM_NUM(1).md)
[MAIL_xxx_ITEM_NUM(2)](D:/md_files/MAIL_xxx_ITEM_NUM(2).md)
---
