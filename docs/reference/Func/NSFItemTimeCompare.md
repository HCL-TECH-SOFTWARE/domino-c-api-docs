##### Function : Item (Field)
##### NSFItemTimeCompare - Compare TYPE_TIME item value to a TIMEDATE.
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFItemTimeCompare(

	NOTEHANDLE  note_handle,
	const char far *item_name,
	const TIMEDATE far *td_item_ptr,
	int far *result_ptr);
```
**Description :**

This function takes a handle to an open note, the name for the TYPE_TIME Item 
whose value you wish to compare,  the TIMEDATE value to be used in the 
comparison.  It returns a value that indicates the result of the comparison: -1 
means the specified TIMEDATE value to be used in the comparison is older,  0 
means they are equal, and 1 means the specified TIMEDATE value to be used in 
the comparison is later.

**Parameters :**
Input :
note_handle  -  A handle to an open note in memory.

item_name  -  The address of a null-terminated item name.

td_item_ptr  -  The address of a TIMEDATE variable containing the TIMEDATE value to be used in the comparison.  If NULL is provided, then the current system Time/Date will be used for the comparison.  If a pointer to a TIMEDATE_PAIR is provided, then the comparison will be made using the first member of the that structure.

Output :
(routine)  -  Returns TRUE if the comparison was successfully done; returns FALSE if the item was not found or if the item is not of TYPE_TIME.


result_ptr  -  The address of the int containing outcome of the comparison: -1 means the td_item_ptr TIMEDATE is older, 0 means they are the same, and 1 means the td_item_ptr TIMEDATE is later.


**Sample Usage :**
```
/* Compare time in Note to current time */

OSCurrentTIMEDATE(&current_td);
printf("Can TIMEDATE in Note be equal to current TIMEDATE?\n");
if (NSFItemIsPresent(note1_handle, TIME_ITEM, strlen(TIME_ITEM)))
{
   NSFItemTimeCompare(note1_handle, TIME_ITEM,
                         &current_td, &answer);
   if (answer == 0)
      printf("Answer: %s\n", "YES YES YES!");
   else if(answer != 0)
      printf("Answer: %s\n", "Nooooooooo!");
}
```
**See Also :**
[NSFItemGetTime](/domino-c-api-docs/reference/Func/NSFItemGetTime)
[NSFItemLongCompare](/domino-c-api-docs/reference/Func/NSFItemLongCompare)
[NSFItemSetTime](/domino-c-api-docs/reference/Func/NSFItemSetTime)
[NSFItemTextEqual](/domino-c-api-docs/reference/Func/NSFItemTextEqual)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
---
