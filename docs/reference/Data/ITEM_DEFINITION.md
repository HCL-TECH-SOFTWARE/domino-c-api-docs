##### Data Type : Item (Field) Information
##### ITEM_DEFINITION - Database Item Definition Table Entry
---
```
#include <nsfdb.h>
```
**Description :**

The Item Definition Table for a database contains the definition for all the 
names and labels defined in a database.  The Item Definition Table consists of 
a header, defined by the structure ITEM_DEFINITION_TABLE, an array of 
ITEM_DEFINITION entries (one for each item), and a packed character array (no 
delimiters or separators) of the names of all the items.  The fields in the 
ITEM_DEFINITION structure are:

        ItemType               What this item represents - type codes are 
defined in nsfdata.h
        NameLength        Length of the item's name, in bytes


**Sample Usage :**
```
/*
 *  GetItemDef
 *
 * Get the entry for an item in the ItemDefTable.  You can
 * access all the items in the table by passing an index of 0
 * through tablePtr->Items - 1.  The data returned consists of
 * a pointer to the ITEM_DEFINITION and a pointer to the name
 * string.  Note that the name string is NOT null-terminated!
 */

int GetItemDef (
   ITEM_DEFINITION_TABLE far *tablePtr, /* In: table address */
   int   i,    /* In: which entry */
   ITEM_DEFINITION far * *itemPtrPtr, /* Out: address of item */
   char   far * *namePtrPtr /* Out: address of name */
) {
   int   j;
   int   nameOffset;
   ITEM_DEFINITION far *curItemPtr;
   char   far *stringPtr;

 /* Check table limits */
   if ((0 > i) || (i >= tablePtr->Items))
 return (-1);

 /* Get the address of the first ITEM_DEFINITION */
   curItemPtr = (ITEM_DEFINITION far *) (((char far *) tablePtr)
 + sizeof (ITEM_DEFINITION_TABLE));

 /* Get the address of the packed name strings array */
   stringPtr = (char far *) (((char far *) tablePtr)
	+ sizeof (ITEM_DEFINITION_TABLE)
 + (tablePtr->Items * sizeof (ITEM_DEFINITION)));
 
 /* Scan the table for the entry and name we need */
   for (j = 0; j < i; j++)
   {
 stringPtr += curItemPtr->NameLength;
 curItemPtr++;
   }
 
   *itemPtrPtr = curItemPtr;
   *namePtrPtr = stringPtr;
 
   return (0);
}
```
**See Also :**
[ITEM_DEFINITION_TABLE](/reference/Data/ITEM_DEFINITION_TABLE)
[NSFDbItemDefTable](/reference/Func/NSFDbItemDefTable)
---
