##### Symbolic Value : Views
##### READ_MASK_xxx - Information returned by NIFReadEntries.
---
```
#include <nif.h>
```
**Description :**

These flags control what information is returned by NIFReadEntries for each 
note that is found. All of the information requested is returned in the buffer 
that NIFReadEntries creates.

The return buffer consists of:

1) The COLLECTIONSTATS structure, if requested by READ_MASK_COLLECTIONSTATS. 
This structure is returned only once at the beginning of the buffer, and is not 
repeated for each note.

2) Information about each note. Each flag requests a different bit of 
information about the note.  If more than one flag is defined, the values 
follow each other, in the order in which the bits are listed here.  This 
portion repeats for as many notes as are found.

**See Also :**
[ITEM_TABLE](/domino-c-api-docs/reference/Data/ITEM_TABLE)
[ITEM_VALUE_TABLE](/domino-c-api-docs/reference/Data/ITEM_VALUE_TABLE)
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
