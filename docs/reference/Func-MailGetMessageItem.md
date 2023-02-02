##### Function : Mail Gateway
##### MailGetMessageItem - Returns the value of a text header item.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailGetMessageItem(**

	DHANDLE  hMessage,
	WORD  ItemCode,
	char far *retString,
	WORD  StringSize,
	WORD far *retStringLength);
**Description :**
This function returns the value of a text header item.

If the item text is larger than the buffer size, the returned string is 
truncated.

If the item is a text list, a concatenation of the values in a text list (with 
commas as delimiters) is returned.

If the item is not a text or text list item, a zero-length string is returned.

This function should generally only be used for items that are known to be 
relatively small (less than 1KB), since it requires a fixed length buffer.  The 
MailGetMessageItemHandle should typically be used for text lists and items that 
can be large since it returns a pointer to the item instead of copying, as 
MailGetMessageItem does.
**Parameters :**
Input :
hMessage  -  Open message handle.

ItemCode  -  Item code (MAIL_xxx_ITEM_NUM).

StringSize  -  Text string buffer size.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


retString  -  Text string value (null-terminated).

retStringLength  -  Text string length (not including '\0').

**Sample Usage :**
```
char        String[MAXSPRINTF+1];
WORD        StringLength;


/* From */
MailGetMessageItem (hMessage, MAIL_FROM_ITEM_NUM, String, 
                                MAXSPRINTF, &StringLength);
String[StringLength] = '\0';
printf ("\tFrom: %s\n", String);
```
**See Also :**
[MailGetMessageItemHandle](D:/md_files/MailGetMessageItemHandle.md)
[MAIL_xxx_ITEM_NUM(1)](D:/md_files/MAIL_xxx_ITEM_NUM(1).md)
[MAIL_xxx_ITEM_NUM(2)](D:/md_files/MAIL_xxx_ITEM_NUM(2).md)
---
