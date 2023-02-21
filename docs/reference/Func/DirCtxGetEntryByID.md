##### Function : Dir
##### DirCtxGetEntryByID - Get the requested items for the entry specified by entryId. 
---
```
#include <dirctx.h>
STATUS LNPUBLIC DirCtxGetEntryByID(

	DIRCTX  hCtx,
	const char *entryId,
	const char *items,
	WORD  numItems,
	DIRENTRY *hEntry);
```
**Description :**

This routine is typically used after a NAMELookup operation to convert the 
$$DirEntryID item it returns into an hEntry object that can be used on a 
subsequent modify operation. In this case specify items as NULL to prevent a 
lookup to the directory server (the hEntry will be a minimal entry that just 
references the entry in the directory). 
         It is also useful for returning a larger set of information about the 
entry than what was asked for on the preceding NAMELookup. 

**Parameters :**
Input :
hCtx  -  Directory context for this operation.

entryId  -  Unique object identifier of the entry to be obtained. This is typically obtained from a preceding NAMELookup() operation.

items  -  A list of specific items, separated by a null character, to be returned. Or, if all items are desired the caller may specify DIR_ITEMS_ALL_DOMINO. If NULL is specified then only the Notes DN is returned for each match in hCollection, and the number of matches are returned in numMatches. 
The order of the items in the list determines the index position that is specified in subsequent calls to DirEntryGetItem() in order to get the values of the items. 
Note that Domino ad hoc items must be asked for specifically. This is so that the existing buffer management code does not have to change significantly. For efficiency and speed this code depends on knowing all the items to be placed in the buffer when the first match is added. This is difficult or at least inefficient if there are multiple matches and the ad-hoc attributes differ between some/all the matches.

numItems  -  The number of items in the list of items to be returned. Specify 1 if one of the DIR_ITEMS_ values is specified. Specify 0 if items is NULL.

Output :
(routine)  -  Status code: 
NOERROR on success. 
An ERR status on failure indicating the problem. 


hEntry  -  Handle to the allocated entry. 
Use DirEntryFree() when done with this entry.


**See Also :**
[DirEntryDelete](/domino-c-api-docs/reference/Func/DirEntryDelete)
[DirEntryFree](/domino-c-api-docs/reference/Func/DirEntryFree)
---
