##### Data Type : Item (Field)
##### ITEM_NAME_TABLE - Header for list of item names.
---
##### #include <nsfdata.h>
**Description :**
	This is the header for lists of item names.

This structure is followed by an array of WORD values containing the lengths, 
in bytes, of the item names;  there is one WORD for each item name in the 
table.  The array is followed, in turn, by the item names as packed data.
**See Also :**
[NIFReadEntries](D:/md_files/NIFReadEntries.md)
[READ_MASK_xxx](D:/md_files/READ_MASK_xxx.md)
---
