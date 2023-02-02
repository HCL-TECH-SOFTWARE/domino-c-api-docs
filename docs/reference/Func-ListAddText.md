##### Function : Text List Manipulation
##### ListAddText - Add a string to a empty text list entry.
---
##### #include <textlist.h>
STATUS LNPUBLIC **ListAddText(**

	void far *pList,
	BOOL  fPrefixDataType,
	WORD  EntryNumber,
	const char far *Text,
	WORD  TextSize);
**Description :**
This function adds a string to an entry in a text list that does not currently 
have a string associated with it.  The list must be of sufficient size, so that 
the unused portion can accommodate the new text string.  Use ListAddEntry if 
there is not already pre-allocated space for the new text string to be added to 
an existing entry.

This function may be used to add text to an existing text list item.  First use 
OSLockBlock on the value_blockid returned by NSFItemInfo for the text list 
item.  The pointer returned by OSLockBlock contains the address of the text 
list within the note.  ListAddText can then be used to add the new text string 
to the text list item.

This function can be used to substitute text for a list entry if the old and 
new text strings are the same length.
**Parameters :**
Input :
pList  -  Pointer to memory containing the original text list.

fPrefixDataType  -  BOOL indicating whether or not the list is prefixed with a WORD containing the Domino data type.  TRUE when using a pointer value derived from a BLOCKID obtained from NSFItemInfo or FALSE if using a pointer value to a newly created list, that will later be added to a note using NSFItemAppend.

EntryNumber  -  WORD containing the entry number (0-based) to be used.  The value must fall between 0 and (ListGetNumEntries - 1).

Text  -  Pointer to memory containing LMBCS characters.  The string does not have to be null-terminated.

TextSize  -  WORD containing the length of the string.  Strings added to the list may be of varying length, but in no case should the length of the new string exceed the amount of available storage in the list.  This amount can be determined using the following algorithm:  ListGetSize - sizeof(LIST) - (sizeof(WORD) * ListGetNumEntries).

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include:

NOERROR - string successfully added to text list.
ERR_MARKERS_FOLLOW - string was too large, overwrote non-list memory.


pList  -  Pointer to memory containing the updated text list.

**Sample Usage :**
```

   if (error_status = ListAddText(old_list_ptr, old_prefix_flag,
                                  FIRST_ENTRY,
                                  STRINGX, strlen(STRINGX)))
       goto Exit;

```
**See Also :**
[ListAllocate](D:/md_files/ListAllocate.md)
[ListGetText](D:/md_files/ListGetText.md)
[ListRemoveEntry](D:/md_files/ListRemoveEntry.md)
[ListAddEntry](D:/md_files/ListAddEntry.md)
[ListGetSize](D:/md_files/ListGetSize.md)
[ListGetNumEntries](D:/md_files/ListGetNumEntries.md)
---
