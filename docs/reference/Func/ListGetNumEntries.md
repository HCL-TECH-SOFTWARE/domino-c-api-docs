##### Function : Text List Manipulation
##### ListGetNumEntries - Returns the number of entries in a text list.
---
```
#include <textlist.h>
WORD LNPUBLIC ListGetNumEntries(

	void far *vList,
	BOOL  NoteItem);
```
**Description :**

This function takes the list pointer and a data type prefix flag.  It returns 
the number of entries in the text list.  The number returned can be used as the 
entry number argument to the ListAddEntry function to insure the appropriate 
entry number is provided to that function call.

**Parameters :**
Input :
vList  -  A pointer to an existing text list.

NoteItem  -  BOOL indicating presence of a Domino data type prefix.   Use FALSE if the first argument is a list that is later going to used in conjunction with NSFItemAppend. Use TRUE if you obtained the list's item and value BLOCKIDs with NSFItemInfo and wish to find out how many entries there are in the list.

Output :
(routine)  -  Returns number of entries in the text list.



**Sample Usage :**
```

   if(error_status = ListAddEntry(list_handle, prefix_flag,&list_size,
                               ListGetNumEntries(list_ptr,prefix_flag),
                               STRING2, strlen(STRING2)))
        goto Exit;

```
**See Also :**
[ListAddEntry](/domino-c-api-docs/reference/Func/ListAddEntry)
[ListAddText](/domino-c-api-docs/reference/Func/ListAddText)
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[ListGetSize](/domino-c-api-docs/reference/Func/ListGetSize)
[ListGetText](/domino-c-api-docs/reference/Func/ListGetText)
[ListRemoveEntry](/domino-c-api-docs/reference/Func/ListRemoveEntry)
---
