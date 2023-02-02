##### Function : Item (Field)
##### NSFNoteHasReadersField - Check whether a note has a readers field.
---
##### #include <nsfnote.h>
BOOL **NSFNoteHasReadersField(**

	DHANDLE  hnote,
	BLOCKID  retbhItem);
**Description :**
Scan all items in a note and check whether the note has at least one item type 
that is ITEM_READERS.
**Parameters :**
Input :
hnote  -  It is an open Note handle.

Output :
(routine)  -  Returns TRUE, if note has at least one item type ITEM_READERS. 
                   FALSE, if no ITEM_READERS type present.


retbhItem  -  If ITEM_READERS field is present then the BLOCKID of first object item is returned.

**Sample Usage :**
```
	/* hnote is an opened document of NOTEHANDLE type. */ 
	BLOCKID bhRFItem; /* Store block id of first item with readers type. */ 
	if (NSFNoteHasReadersField(hnote, &bhRFItem)) 
	{ 
	 printf("Document has at least one reader field"); 
	} 
	else 
	{ 
	 printf("Document has no reader fields"); 
	}
```
**See Also :**
[](D:/md_files/.md)
---
