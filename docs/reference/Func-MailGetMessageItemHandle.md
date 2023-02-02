##### Function : Mail Gateway
##### MailGetMessageItemHandle - Returns a handle to the value for a message header item.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailGetMessageItemHandle(**

	DHANDLE  hMessage,
	WORD  ItemCode,
	BLOCKID far *retbhValue,
	WORD far *retValueType,
	DWORD far *retValueLength);
**Description :**
This function returns a handle ("block ID" or pool handle and offset) to the 
value for a specified message header item.  The item can be of any data type.  
The caller can use the OS Pool functions to obtain a pointer to the value of 
the item.

The BLOCKID value obtained using this function refers to memory within a note.  
This memory is managed by Domino, and should not be freed by the application.
**Parameters :**
Input :
hMessage  -  Open message handle.

ItemCode  -  Item code; all of the MAIL_xxx_ITEM_NUM codes are valid.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


retbhValue  -  Item value handle.

retValueType  -  Item value data type (TYPE_xxx).

retValueLength  -  Item value length in bytes.

**See Also :**
[MailGetMessageItem](D:/md_files/MailGetMessageItem.md)
[MAIL_xxx_ITEM_NUM(1)](D:/md_files/MAIL_xxx_ITEM_NUM(1).md)
[MAIL_xxx_ITEM_NUM(2)](D:/md_files/MAIL_xxx_ITEM_NUM(2).md)
---
