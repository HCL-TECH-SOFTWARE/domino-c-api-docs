##### Function : Item (Field)
##### NSFItemGetTextListEntries - Return number of entries in TYPE_TEXT_LIST item.
---
```
#include <nsfnote.h>
WORD LNPUBLIC NSFItemGetTextListEntries(

	NOTEHANDLE  note_handle,
	const char far *item_name);
```
**Description :**

This function takes a handle to an open note and the name for the text list 
Item from which to  obtain the number of text list entries. The function 
returns the number of entries in the text list item.

**Parameters :**
Input :
note_handle  -  A handle to an open note in memory.

item_name  -  A pointer to a null-terminated Item name.

Output :
(routine)  -  Return the number of entries in the text list.



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
[NSFItemAppendTextList](/reference/Func/NSFItemAppendTextList)
[NSFItemCreateTextList](/reference/Func/NSFItemCreateTextList)
[NSFItemGetTextListEntry](/reference/Func/NSFItemGetTextListEntry)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
[ListGetNumEntries](/reference/Func/ListGetNumEntries)
---
