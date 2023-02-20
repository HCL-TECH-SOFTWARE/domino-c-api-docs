##### Function : Item (Field)
##### NSFItemGetText - Get the value of  a TYPE_TEXT item.
---
```
#include <nsfnote.h>
WORD LNPUBLIC NSFItemGetText(

	NOTEHANDLE  note_handle,
	const char far *item_name,
	char far *item_text,
	WORD  text_len);
```
**Description :**

This function takes a handle to an open note and the name of a text item whose 
value you wish to get.  The function copies the text item into a buffer 
provided by you, and returns the length of the text that was retrieved. 
If the buffer is smaller than the text item, the text item will be truncated 
and the returned length will be the length of the truncated item.

The retrieved text may contain embedded null ('\0') characters. Notes uses null 
characters (a char with value zero) to designate newlines. You must convert the 
null characters to the appropriate newline character for your system before 
printing out the retrieved text.

NOTE: This function does not distinguish between an item with zero length and 
an item that does not exist. In both cases, NSFItemGetText returns a length of 
zero. You may use NSFItemIsPresent to see if an item exists.

**Parameters :**
Input :
note_handle  -  A handle to an open note.

item_name  -  A pointer to a null-terminated item name.

text_len  -  A WORD containing the length of the text buffer. 

Output :
(routine)  -  Length of the text that was retrieved.


item_text  -  The address of a text buffer in which the item's contents will be returned.


**Sample Usage :**
```
field_len = NSFItemGetText ( 
                hNote, 
                ITEM_NAME_CATEGORIES,
                field_text,
                sizeof (field_text));
```
**See Also :**
[NSFItemSetText](/reference/Func/NSFItemSetText)
[NSFItemTextEqual](/reference/Func/NSFItemTextEqual)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
[NSFItemInfo](/reference/Func/NSFItemInfo)
---
