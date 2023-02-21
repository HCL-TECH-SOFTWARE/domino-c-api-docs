##### Function : Item (Field)
##### NSFItemGetTextListEntry - Get an entry from a TYPE_TEXT_LIST Item.
---
```
#include <nsfnote.h>
WORD LNPUBLIC NSFItemGetTextListEntry(

	NOTEHANDLE  note_handle,
	const char far *item_name,
	WORD  entry_position,
	char far *entry_text,
	WORD  text_len);
```
**Description :**

This function takes a handle to an open note, the name for the text list Item 
from which you wish to obtain a particular entry, the position of the entry in 
the text list, and the length of the text buffer that will receive the entry 
text.  It returns the entry text in the buffer provided and  the function 
itself returns the length of the entry.

**Parameters :**
Input :
note_handle  -  A handle to an open note in memory.

item_name  -  A pointer to a null-terminated Item name.  

entry_position  -  A WORD containing the ordinal position of the desired text list entry.  0 is the first position/entry in a text list Item.

text_len  -  A WORD containing the length of the buffer - 1 (to allow for the mandatory null termination).

Output :
(routine)  -  Returns the length of the desired text list entry.


entry_text  -  A pointer a buffer to receive the text list entry's string.


**Sample Usage :**
```
/* Print the TEXT_LIST_ITEM */

num_entries = NSFItemGetTextListEntries(note1_handle,
                                           TEXT_LIST_ITEM);
for (counter = 0; counter < num_entries; counter++)
{
   text_len = NSFItemGetTextListEntry(note1_handle,
                    TEXT_LIST_ITEM, counter, text_buf2, LINEOTEXT-1);
   text_buf2[text_len] = '\0';
   printf("%s[%u]: %s\n", TEXT_LIST_ITEM, counter, text_buf2);
}
```
**See Also :**
[NSFItemAppendTextList](/domino-c-api-docs/reference/Func/NSFItemAppendTextList)
[NSFItemCreateTextList](/domino-c-api-docs/reference/Func/NSFItemCreateTextList)
[NSFItemGetTextListEntries](/domino-c-api-docs/reference/Func/NSFItemGetTextListEntries)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[ListGetText](/domino-c-api-docs/reference/Func/ListGetText)
---
