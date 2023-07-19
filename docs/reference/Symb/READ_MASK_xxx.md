##### Symbolic Value : Views
##### READ_MASK_xxx - Information returned by NIFReadEntries.
---
```
#include <nif.h>
```

**Symbolic Values :**

	READ_MASK_NOTEID	  -  NOTEID of note

	READ_MASK_NOTEUNID	  -  UNID of note.

	READ_MASK_NOTECLASS	  -  Note class of note. Occupies one WORD in the buffer.

	READ_MASK_INDEXSIBLINGS	  -  Number of siblings in view or folder. Occupies one DWORD in the buffer.

	READ_MASK_INDEXCHILDREN	  -  Number of immediate children in view or folder. Subcategories are included in the count. Occupies one DWORD in the buffer.

	READ_MASK_INDEXDESCENDANTS	  -  Number of descendents in view or folder. Subcategories are not included in the count. Occupies one DWORD in the buffer.

	READ_MASK_INDEXANYUNREAD	  -  TRUE if unread (or any descendents unread), FALSE otherwise. Occupies one WORD in the buffer.

	READ_MASK_INDENTLEVELS	  -  Number of levels that this entry should be indented in a formatted view or folder. Occupies one WORD in the buffer.

	READ_MASK_SCORE	  -  Relevancy score of an entry. Occupies one WORD in the buffer. FTSearch must be called prior to NIFReadEntries. The FT_SEARCH_SET_COLL search option or'd with the FT_SEARCH_SCORES search option must be specified in the call to FTSearch.

	READ_MASK_INDEXUNREAD	  -  TRUE if this entry is unread, FALSE otherwise. Occupies one WORD in the buffer.

	READ_MASK_COLLECTIONSTATS	  -  Collection statistics (as a COLLECTIONSTATS structure).

	READ_MASK_INDEXPOSITION	  -  Truncated COLLECTIONPOSITION. Use COLLECTIONPOSITIONSIZE macro to determine the size it occupies in the buffer.

	READ_MASK_SUMMARYVALUES	  -  Summary buffer of summary data values that appear in the view. The data is in the format of an ITEM_VALUE_TABLE. This format consists of an ITEM_VALUE_TABLE followed by an array of WORD values containing the lengths, in bytes, of the data items; there is one WORD for each item in the table. The data length table is followed, in turn, by a packed sequence of item values. Each item value includes the item's datatype. The item's datatype is stored in the first USHORT of each item value.

	READ_MASK_SUMMARY	  -  Summary buffer of summary data values that appear in the view. The data is in the format of an ITEM_TABLE. This format consists of an ITEM_TABLE structure, followed by an array of ITEM structures, followed by packed pairs, where each pair consists of the item name followed by the item value. Each item value includes the item's datatype. The item's datatype is stored in the first USHORT of each item value.


**Description :**

These flags control what information is returned by NIFReadEntries for each note that is found. All of the information requested is returned in the buffer that NIFReadEntries creates.<br>
<br>
The return buffer consists of:<br>
<br>
1) The COLLECTIONSTATS structure, if requested by READ_MASK_COLLECTIONSTATS. This structure is returned only once at the beginning of the buffer, and is not repeated for each note.<br>
<br>
2) Information about each note. Each flag requests a different bit of information about the note.  If more than one flag is defined, the values follow each other, in the order in which the bits are listed here.  This portion repeats for as many notes as are found.


**See Also :**
[ITEM_TABLE](/domino-c-api-docs/reference/Data/ITEM_TABLE)
[ITEM_VALUE_TABLE](/domino-c-api-docs/reference/Data/ITEM_VALUE_TABLE)
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
