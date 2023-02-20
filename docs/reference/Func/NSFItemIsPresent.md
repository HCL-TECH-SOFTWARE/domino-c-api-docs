##### Function : Item (Field)
##### NSFItemIsPresent - Return TRUE if an Item is present in a note.
---
```
#include <nsfnote.h>
BOOL NSFItemIsPresent(

	NOTEHANDLE  note_handle,
	char far *item_name,
	WORD  item_name_length);
```
**Description :**

This function takes a handle to an open note and the name for the Item whose 
presence you wish to confirm, and the length of that name.  If the Item is 
present it returns TRUE.

**Parameters :**
Input :
note_handle  -  A handle to an open note in memory.

item_name  -  A pointer to an Item name string.

item_name_length  -  The length of the item_name string.

Output :
(routine)  -  TRUE - If named Item is present in the open note.  FALSE - If named item is NOT present in the open note.



**Sample Usage :**
```

  /* Print ULONG ITEM */
 
  if (NSFItemIsPresent(note1_handle,ULONG_ITEM, strlen(ULONG_ITEM)))
       printf("%s: %lu\n", ULONG_ITEM,
              (NSFItemGetLong(note1_handle, ULONG_ITEM, 0L)));


```
**See Also :**
[NSFItemInfo](/reference/Func/NSFItemInfo)
[NSFItemInfoNext](/reference/Func/NSFItemInfoNext)
[NSFItemQuery](/reference/Func/NSFItemQuery)
[NSFItemScan](/reference/Func/NSFItemScan)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
---
