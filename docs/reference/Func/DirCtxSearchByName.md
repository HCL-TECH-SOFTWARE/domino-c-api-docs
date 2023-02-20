##### Function : Dir
##### DirCtxSearchByName - Search for one or more directory entries by name. 
---
```
#include <dirctx.h>
STATUS LNPUBLIC  DirCtxSearchByName(

	DIRCTX  hCtx,
	const char *name,
	const char *items,
	WORD  numItems,
	DIRCOLLECTION *hCollection);
```
**Description :**

Search for one or more directory entries by name. 
The potential types of entries returned include people, groups, mail-in 
databases, servers, rooms, and resources. 

**Parameters :**
Input :
hCtx  -  Directory context for this operation.

name  -  Name of the entry to be searched for. This can be the Notes distinguished name, abbreviated name, common name, first name, last name, internet address,email address, or shortname of an entry. Must not be NULL or "".

items  -  A list of specific items, separated by a null character, to be returned. Or, if all items are desired the caller may specify DIR_ITEMS_ALL_DOMINO. If NULL is specified then only the Notes DN is returned for each match in hCollection, and the number of matches are returned in numMatches. 
The order of the items in the list determines the index position that is specified in subsequent calls to DirEntryGetItem() in order to get the values of the items. 
Note that Domino ad hoc items must be asked for specifically. This is so that the existing buffer management code does not have to change significantly. For efficiency and speed this code depends on knowing all the items to be placed in the buffer when the first match is added. This is difficult or at least inefficient if there are multiple matches and the ad-hoc attributes differ between some/all the matches.

numItems  -  The number of items in the list of items to be returned. Specify 1 if one of the DIR_ITEMS_ values is specified. Specify 0 if items is NULL.

Output :
(routine)  -  Status code: 
NOERROR on success. 
An ERR status on failure indicating the problem. 


hCollection  -  Handle to an allocated collection of entries that match the search criteria. If there are no matching entries, NOERROR will be returned and a non-NULL DIRCOLLECTION is returned in hCollection. 
Callers should not call DirEntryFree() on the returned directory entry objects! They will be indirectly freed by calling DirCollectionFree().


**See Also :**
[DirCtxSearchDominoGroupsByName](/reference/Func/DirCtxSearchDominoGroupsByName)
[DirCtxSearchDominoPersonsByName](/reference/Func/DirCtxSearchDominoPersonsByName)
[DirCtxSearchGroupsByName](/reference/Func/DirCtxSearchGroupsByName)
[DirCtxSearchPersonsByName](/reference/Func/DirCtxSearchPersonsByName)
---
