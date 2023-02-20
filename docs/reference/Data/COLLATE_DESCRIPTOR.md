##### Data Type : Views
##### COLLATE_DESCRIPTOR - Defines the sort criteria for each column in a view.
---
```
#include <nifcoll.h>
```
**Description :**

The COLLATE_DESCRIPTOR structure is one of the components of the view collation 
item in a view note. The view collation item is an item of TYPE_COLLATION with 
item name VIEW_COLLATION_ITEM ($Collation).

The $Collation item consists of a COLLATION structure (defined elsewhere in 
this database), followed by an array of one or more COLLATE_DESCRIPTOR 
structures (one for each sorted column), followed by an array of packed 
character strings referenced by the descriptors.

Flags:             Specifies whether the column will be sorted in ascending or 
descending order, and whether the sort will be case or accent sensitive. 
signature:       Must be COLLATE_DESCRIPTOR_SIGNATURE.
keytype:         Specifies how to sort column - by key, by category, etc.
NameOffset   Offset into text array of the string specifying the item name of 
the column to be sorted.
NameLength  Length of the name string.

Note that the $Collation item in a view note is of type TYPE_COLLATION. 
Therefore, portable API programs must convert this item value to Domino 
canonical format before appending the item to the view note, and convert the 
item value to Host format after reading the item from a view note.

This entry is repeated in a collating specification for each "key" which wants 
to be collated. The key name is the name string of the item in the note summary 
information.

 The entries are placed in the list in the order in which the collating is to 
be done. Thus, the first entry in the list has the highest priority, second has 
next highest priority, etc.  The collating routine only continues down the list 
of items as long as the higher priority items match exactly.

 The KEY,TUMBLER,CATEGORY collating types compares two entries using the value 
of the specified item as the collating value. The others use data found within 
the NODE itself to collate two entries, rather than using item values.

 There are special meanings associated with the TUMBLER and CATEGORY types. 
Like the KEY, they sort based on a summary item's value.  However:

 1) TUMBLER is used with "list" item datatypes (non-list datatypes are treated 
exactly the same as a KEY). Each value of the list corresponds to a level in a 
hierarchical (outline) index.  As collation is performed, only the "i"th list 
value is collated if we are collating the "i"th level of the hierarchical 
index.  This causes the new index entry to be placed as many levels deep as 
there are list values.

 As an example, a number list value of "1:2:3" places the index entry 3 levels 
down in the hierarchy. If the new index entry requires a subtree which does not 
yet exist, a "ghost" entry is created to act as a parent for the new entry at 
intermediate levels. The result is an hierarchical outline where index entries 
are created at a variety of different levels in the index depending on the 
number of values in their list datatype.

 2) CATEGORY is used with any datatypes (list or non-list) to create a 
hierarchical index.  For each CATEGORY in the collating spec, "ghost" entries 
are created for each UNIQUE value of the specified item (only as many "ghost" 
entries as there are unique values), and all duplicate values are placed at the 
next lower level.

 Unlike TUMBLER, CATEGORY collates list datatypes exactly the same way as KEY, 
which is that each list value is compared, and only if equal, the next one is 
compared to break ties, and so on until the list is exhausted.

 As an example, if a collating spec consists of 1) CATEGORY "Folder", 2) 
CATEGORY "Author", and 3) KEY "Date", the top level of the index will only 
contain as many "ghost" entries as there are unique Folder names, and below it, 
the next level will contain all unique Author names within that folder, and 
below each Author, the next level will contain all the actual index entries for 
each Author sorted by Date. The result is a 3-level hierarchical outline where 
all index entries are always at the "n"th level, and all intermediate 
"category" levels always contain only "ghost" entries.

**Sample Usage :**
```

COLLATION          Collation;
COLLATE_DESCRIPTOR CollateDesc;
COLLATE_DESCRIPTOR CollateDesc2;
WORD   wCollationBufLen;
HANDLE hCollationBuffer;
char  *pCollationBuffer;
char  *pCBuf;


wCollationBufLen =  ODSLength( _COLLATION )          +
                    ODSLength( _COLLATE_DESCRIPTOR ) +
                    ODSLength( _COLLATE_DESCRIPTOR ) +
                    wItemName_1_Len                  +
                    wItemName_2_Len                  ;

OSMemAlloc( 0, wCollationBufLen, &hCollationBuffer );

pCollationBuffer = OSLockObject( hCollationBuffer );

pCBuf = (void *)pCollationBuffer;

/* ... steps missing ... */
    
/*
 *  Initialize the collation descriptor for the first column. The
 *  first column is a category.
 */

CollateDesc.Flags = 0;   
CollateDesc.signature = COLLATE_DESCRIPTOR_SIGNATURE;
CollateDesc.keytype = COLLATE_TYPE_CATEGORY;
CollateDesc.NameOffset = 0;
CollateDesc.NameLength = wItemName_1_Len;

/*
 * Convert the collation descriptor for the first column to Domino 
 * canonical format, and store it in the buffer. This increments
 * pCBuf to point to the next byte in the buffer after the collation
 * descriptor.
 */

ODSWriteMemory( &pCBuf, _COLLATE_DESCRIPTOR, &CollateDesc, 1 );

/* ... steps missing ... */

/*
 *  Now append the $COLLATION item to the note.
 */
    
sError = NSFItemAppend( hNote,
                        ITEM_SUMMARY,
                        VIEW_COLLATION_ITEM,
                        sizeof(VIEW_COLLATION_ITEM) - 1,
                        TYPE_COLLATION,
                        pCollationBuffer,
                        (DWORD) wCollationBufLen );

OSUnlockObject( hCollationBuffer);
OSMemFree( hCollationBuffer );
```
**See Also :**
[COLLATION](/reference/Data/COLLATION)
[ODSWriteMemory](/reference/Func/ODSWriteMemory)
[_xxx (ODS Types)](/reference/Symb/_xxx (ODS Types))
[CDF_xxx](/reference/Symb/CDF_xxx)
---
