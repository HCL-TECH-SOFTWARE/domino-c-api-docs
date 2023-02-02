##### Function : Dir
##### DirEntryGetItemByName - Get the value(s) of an item in an entry based on the item name. 
---
##### #include <direntry.h>
STATUS LNPUBLIC **DirEntryGetItemByName(**

	DIRENTRY  hEntry,
	const char *itemName,
	WORD *pItemDataType,
	DHANDLE *phItemValue,
	DWORD *pItemValLen);
**Description :**
Note that this routine must first determine the index of the item corresponding 
to itemName in order to get the value of that item. For this reason it is 
slower that DirEntryGetItem(), which can access the value directly with the 
index provided by the caller. Callers are encouraged to use DirEntryGetItem() 
whenever possible.
**Parameters :**
Input :
hEntry  -  Handle to the entry whose item is to be returned. If hEntry is NULLDIRENTRY then NULL is returned.

itemName  -  The name of the item to get.

Output :
(routine)  -  
NOERROR 



ERR_NO_SUCH_ITEM 
If item was not requested in Search. 

ERR_DIR_NULL_ENTRY 
If hEntry is NULL. 

ERR_DIR_NULL_ARGUMENT 
If itemName is NULL. 

... 
An ERR status on failure indicating the problem. 



pItemDataType  -  The Notes data type of the item. See the section on Data Types.

phItemValue  -  handle is returned to the memory containing the value. This memory is allocated for the caller and is up to the caller to free. Note if the item value is 0, this handle will be returned NULL

pItemValLen  -  The size of the value(s) for itemName in bytes.

**See Also :**
[DirEntryGetItem](D:/md_files/DirEntryGetItem.md)
---
