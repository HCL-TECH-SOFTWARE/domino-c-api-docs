##### Function : Dir
##### DirEntryGetItem - Get the value(s) of an item in an entry based on the item index. 
---
```
#include <direntry.h>
STATUS LNPUBLIC  DirEntryGetItem(

	const DIRENTRY  hEntry,
	WORD  itemIndex,
	char *itemName,
	WORD *itemDataType,
	DHANDLE *hItemValue,
	DWORD *itemValLen);
```
**Description :**

Get the value(s) of an item in an entry based on the item index. 
          Note that callers are encouraged to use this routine rather than 
DirEntryGetItemByName(),since it is faster (because of the way the result 
buffer is arranged). 
          Note that this function's status code will reveal if the item exists 
or not even if the caller passes in a NULL hItemValue.

**Parameters :**
Input :
hEntry  -  Handle to the entry whose item is to be returned. If hEntry is NULLDIRENTRY then NULL is returned.

itemIndex  -  The index of the item whose value is to be returned. The index position of items is determined by the order the items were asked for on the search or get operation that returned the entry.

Output :
(routine)  -  
NOERROR

ERR_NO_SUCH_ITEM
If item was not requested in Search. 

ERR_DIR_NULL_ENTRY
If hEntry is NULL. 

...
An ERR status on failure indicating the problem. 



itemName  -  The name of the item returned. The caller must supply a buffer of at least ITEM_NAME_MAX+1 bytes, in which the name of the item will be returned. Specify NULL if not desired.

itemDataType  -  The Notes data type of the item. The possible values returned are the following, taken from nsfdata.h 
TYPE_TEXT, TYPE_TEXT_LIST: Use DirEntryGetTextItem() to get a value 
TYPE_NUMBER, TYPE_NUMBER_RANGE: Use DirEntryGetNumberItem() to get a value 
TYPE_TIME, TYPE_TIME_RANGE: Use DirEntryGetTimeItem() to get a value

hItemValue  -  A handle is returned to the memory containing the value. This memory is allocated for the caller and is up to the caller to free. Note if the item value is 0, this handle will be returned NULL

itemValLen  -  The size of the value(s) for itemName in bytes.


**See Also :**
[DirEntryGetItemByName](/domino-c-api-docs/reference/Func/DirEntryGetItemByName)
---
