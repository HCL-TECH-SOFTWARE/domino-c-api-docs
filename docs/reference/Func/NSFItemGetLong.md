##### Function : Item (Field)
##### NSFItemGetLong - Return value of  TYPE_NUMBER item as a LONG.
---
```
#include <nsfnote.h>
LONG LNPUBLIC NSFItemGetLong(

	NOTEHANDLE  note_handle,
	const char far *number_item_name,
	LONG  number_item_default);
```
**Description :**

This function takes a handle to an open note, the name for the item whose value 
you wish to get and a default value to be returned by the function.

**Parameters :**
Input :
note_handle  -  A handle to an open note in memory.

number_item_name  -  A pointer to a null-terminated item name.

number_item_default  -  The default value to be returned by the function if the item is not present.

Output :
(routine)  -  If TYPE_NUMBER item is present, return the value coerced as a LONG.  If item is not present, return the default value provided in the third argrument.



**Sample Usage :**
```
/* Print ULONG ITEM */

   if (NSFItemIsPresent(note1_handle,ULONG_ITEM, strlen(ULONG_ITEM)))
       printf("%s: %lu\n", ULONG_ITEM,
              (NSFItemGetLong(note1_handle, ULONG_ITEM, 0L)));
```
**See Also :**
[NSFItemGetNumber](/domino-c-api-docs/reference/Func/NSFItemGetNumber)
[NSFItemLongCompare](/domino-c-api-docs/reference/Func/NSFItemLongCompare)
[NSFItemSetNumber](/domino-c-api-docs/reference/Func/NSFItemSetNumber)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
---
