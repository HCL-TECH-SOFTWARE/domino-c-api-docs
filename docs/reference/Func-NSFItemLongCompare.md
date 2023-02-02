##### Function : Item (Field)
##### NSFItemLongCompare - Compare (long) item to a given (long) value.
---
##### #include <nsfnote.h>
BOOL LNPUBLIC **NSFItemLongCompare(**

	NOTEHANDLE  note_handle,
	const char far *item_name,
	long  long _value,
	int far *result_ptr);
**Description :**
This function takes a handle to an open note, the name for the TYPE_NUMBER Item 
whose value you wish to compare,  the (long) value to be used in the 
comparison.  It returns a int whose value indicates the result of the 
comparison: -1 if item (long) is greater, 0 if they are equal, and 1 if item 
(long) is less.
**Parameters :**
Input :
note_handle  -  A handle to an open note in memory.

item_name  -  The address of a null-terminated Item name.

long _value  -  A (long) value you wish to compare with a NUMBER item in the open note.  All values of  TYPE_NUMBER are stored in IEEE floating point format, so the NUMBER item is first coerced into a (long), and then that value (minus the decimal fraction) is used in the comparison.

Output :
(routine)  -  Always returns FALSE.


result_ptr  -  The address of the int containing outcome of the comparison: -1 means the NUMBER item is larger, 0 means they are equal, and 1 means the NUMBER item is smaller.

**Sample Usage :**
```
/* Compare  ULONG in Note to another value */

ulong_num2 = 3430000L;
printf("Is ULONG in Note equal to %lu ?\n", ulong_num2);
if (NSFItemIsPresent(note1_handle, ULONG_ITEM,strlen(ULONG_ITEM)))
{
   NSFItemLongCompare(note1_handle, ULONG_ITEM,
                          (long) ulong_num2, &answer);
   if (answer == 0)
      printf("Answer: %s\n", "YES YES YES!");
   else if(answer != 0)
      printf("Answer: %s\n", "Nooooooooo!");
}
```
**See Also :**
[NSFItemGetLong](D:/md_files/NSFItemGetLong.md)
[NSFItemGetNumber](D:/md_files/NSFItemGetNumber.md)
[NSFItemSetNumber](D:/md_files/NSFItemSetNumber.md)
[NSFItemTextEqual](D:/md_files/NSFItemTextEqual.md)
[NSFItemTimeCompare](D:/md_files/NSFItemTimeCompare.md)
[NSFNoteClose](D:/md_files/NSFNoteClose.md)
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
---
