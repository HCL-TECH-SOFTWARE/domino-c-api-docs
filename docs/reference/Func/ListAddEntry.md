##### Function : Text List Manipulation
##### ListAddEntry - Add a string to a text list.
---
```
#include <textlist.h>
STATUS LNPUBLIC ListAddEntry(

	DHANDLE  hList,
	BOOL  fPrefixDataType,
	WORD far *pListSize,
	WORD  EntryNumber,
	const char far *Text,
	WORD  TextSize);
```
**Description :**

This function adds a string to a text list in memory, increasing number of 
entries in the list if necessary. This re-allocates the storage associated with 
the the text list to the original size plus the specified text size plus one 
more word for the entry length. 

The hlist does not have to be unlocked before this call.  However, this 
function may move the memory object to increase the size of the list.  
Therefore, after returning from this function and before referencing any 
pointers to the text list, the caller MUST refresh all pointers to the text 
list by unlocking the list handle (OSUnlockObject)and then relocking the list 
handle (OSLockObject).  It is recommended that you unlock the list handle after 
the call to ListAllocate and relock the list handle before subsequent 
references to the text list pointer.

This function can not be used to increase the size of a text list item that is 
already part of a note, as the value.blockid.pool member is not the equivalent 
of an hList.

**Parameters :**
Input :
hList  -  HANDLE to a Domino memory object containing text list.  This handle must have been created with ListAllocate.  ListAddEntry does not require that the list be unlocked at the time of the call.

fPrefixDataType  -  BOOL indicating whether or not the list is prefixed with a WORD containing the Domino data type.  The value should be FALSE when used in association with a HANDLE to a newly created list, that will later be added to a note using NSFItemAppend.

pListSize  -  Address of the WORD variable containing the current list size.

EntryNumber  -  WORD containing the value returned by a call to ListGetNumEntries.  Since the entry number is 0-based, the value will always be equal to the next available EntryNumber.

Text  -  Address of the string to be added to the text list.  This string does not have to be null-terminated.

TextSize  -  WORD containing the number of bytes in the string.

Output :
(routine)  -  Return indicates either sucess or what the error is. The return codes include:

NOERROR - list entry was successfully added.
ERR_MEMORY - Not enough global memory available for allocation.
ERR_SEGMENT_TOO_BIG - Requested size is greater than the maximum supported (60K).


pListSize  -  Address of the WORD variable containing the new list size.


**Sample Usage :**
```
ListAllocate(0, 0, FALSE, &hList, &pList, &wListSize);
NumEntries = ListGetNumEntries(pList, FALSE)
OSUnlockObject(hList); 

ListAddEntry(hList, FALSE, &wListSize,
             NumEntries,  
             "NewTextListEntry",
	        strlen("NewTextListEntry"));
pList = OSLockObject (hList);

NSFItemAppend(hNote, ITEM_SUMMARY, FieldName,
              FieldNameLen, TYPE_TEXT_LIST,
              pList, wListSize);
OSUnlockObject(hList);
OSMemFree (hList);
```
**See Also :**
[ListAddText](/reference/Func/ListAddText)
[ListAllocate](/reference/Func/ListAllocate)
[ListGetNumEntries](/reference/Func/ListGetNumEntries)
[ListGetSize](/reference/Func/ListGetSize)
[ListRemoveAllEntries](/reference/Func/ListRemoveAllEntries)
[ListRemoveEntry](/reference/Func/ListRemoveEntry)
---
