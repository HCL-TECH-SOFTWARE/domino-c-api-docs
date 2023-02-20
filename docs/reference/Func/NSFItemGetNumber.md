##### Function : Item (Field)
##### NSFItemGetNumber - Get the value of  TYPE_NUMBER Item.
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFItemGetNumber(

	NOTEHANDLE  hNote,
	const char far *ItemName,
	NUMBER far *retNumber);
```
**Description :**

This function takes a handle to an open note and the name for the Item whose 
value you wish to get.  It returns the Item's value in a FLOAT variable.

**Parameters :**
Input :
hNote  -  A handle to an open note in memory.

ItemName  -  A pointer to a null-terminated item name.

Output :
(routine)  -  TRUE - If Item was present and successfully retrieved.  FALSE  - if Item was not present.


retNumber  -  The address of a NUMBER (or equivalent 'double') variable in which the floating point number retrieved from named Item in the open note will be returned.


**Sample Usage :**
```
/* Print FLOAT ITEM */

double num;
if (NSFItemGetNumber (note1_handle, FLOAT_ITEM, &num))
  printf("%s: %le\n", FLOAT_ITEM, num);
```
**See Also :**
[NSFItemGetLong](/reference/Func/NSFItemGetLong)
[NSFItemLongCompare](/reference/Func/NSFItemLongCompare)
[NSFItemSetNumber](/reference/Func/NSFItemSetNumber)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
---
