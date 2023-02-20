##### Function : Text List Manipulation
##### ListAllocate - Create a text list.
---
```
#include <textlist.h>
STATUS LNPUBLIC ListAllocate(

	WORD  ListEntries,
	WORD  TextSize,
	BOOL  fPrefixDataType,
	DHANDLE far *rethList,
	void far *retpList,
	WORD far *retListSize);
```
**Description :**

This function creates a text list structure in memory that can be populated 
with multiple text strings to create a text list.  It takes as input the number 
of entries to create in the list, a total size to allocate for text storage, 
and a flag indicating whether to allocate an extra WORD for the Domino data 
type prefix.  It allocates and locks a block of memory and initializes the 
memory with a LIST structure and, optionally, the Domino data type word.  It 
returns a handle to the Text List memory object, a pointer to the Text List, 
and the overall size of the memory object.

Upon successful return, the list memory object is locked and a pointer to the 
object is returned in addition to the object's handle.  Since the object is 
returned locked, you must explicitly unlock the object (OSUnlockObject) before 
attempting to free it (OSMemFree). 

Call ListAddText to store up to the specified number of entries in the list.  
Call ListAddEntry to add more entries to the list than the number specified by 
num_entries.

If you append the text list to a document using a function that copies the 
memory, such as NSFItemAppend, then you must subsequently unlock and free the 
memory yourself. If you append the text list to a document using a function 
that takes ownership of the memory, such as NSFItemAppendByBLOCKID or 
MailAddRecipientsItem, then unlock the memory but do not free it.

**Parameters :**
Input :
ListEntries  -  WORD containing the number of list entries to reserve.  0 indicates that no entries should be provided for in advance.

TextSize  -  The size, in bytes, of memory to allocate for storing the text portion of the text list.  0 indicates that no storage space should be provided for in advance. ListAddText requires that the list has enough entrys and sufficient space.  ListAddEntry, however, will re-allocate the memory as necessary if a text item would exceed the pre-allocated space.

fPrefixDataType  -  A flag controlling allocation of Domino data type prefix.  TRUE causes ListAllocate to allocate an additional WORD and to set this WORD to TYPE_TEXT_LIST.  The data type word is the first WORD of the object.  FALSE causes ListAllocate to skip this step.  Use FALSE if your program uses NSFItemAppend to append the item to a document.  Use TRUE if your program uses NSFItemAppendByBLOCKID to append the item to a document.  This BOOL must be the same value for all subsequent calls to List functions that refer to the same list.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include:

NOERROR - list was successfully allocated.
ERR_MEMORY - Not enough global memory available for allocation.
ERR_SEGMENT_TOO_BIG - Requested size is greater than the maximum supported (60K).
ERR_xxx -  STATUS returned from a lower-level function.


rethList  -  Address of a HANDLE in which the handle to the Domino memory object containing the newly created text list is returned.

retpList  -  Pointer to the newly created list.

retListSize  -  Address of a WORD in which the actual size of the newly created text list is returned.  The value returned is  ( (sizeof (WORD) to hold the Domino data type, if requested) + (sizeof(LIST) to hold the LIST structure) + (one WORD for each entry, to hold its length) + (text_size)).


**Sample Usage :**
```

error = ListAllocate(0, 0, TRUE, &hRecipientsItem, &RecipientsItem, 
                    &RecipientsItemSize);
if (error) goto Close;
OSUnlockObject(hRecipientsItem);

while (fgets(String, sizeof(String), ForeignFile))
{
    Code = String[0];
    Value = &String[1];
    ValueLength = strlen(Value);

    error = ListAddEntry(hRecipientsItem, TRUE, 
            &RecipientsItemSize, Recipients, 
            Value, ValueLength);
}
error = MailAddRecipientsItem(hMessage, hRecipientsItem, RecipientsItemSize);
if (error) goto Close;
hRecipientsItem = NULLHANDLE;
```
**See Also :**
[ListAddText](/reference/Func/ListAddText)
[ListGetText](/reference/Func/ListGetText)
[ListRemoveEntry](/reference/Func/ListRemoveEntry)
[ListAddEntry](/reference/Func/ListAddEntry)
[ListGetSize](/reference/Func/ListGetSize)
[ListGetNumEntries](/reference/Func/ListGetNumEntries)
---
