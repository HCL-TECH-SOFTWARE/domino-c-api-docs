##### Function : Dir
##### DirCtxSearchDominoGroupsByName - Search for one or more groups which match the given name. 
---
##### #include <dirctx.h>
STATUS LNPUBLIC **DirCtxSearchDominoGroupsByName(**

	DIRCTX  hCtx,
	const char *name,
	const char *items,
	WORD  numItems,
	DWORD  groupType,
	DIRCOLLECTION *hCollection);
**Description :**
Search for one or more groups which match the given name. 
**Parameters :**
Input :
hCtx  -  Directory context for this operation.

name  -  Name of group(s) to search for. This may be either the Notes distinguished name, abbreviated name, common name, or internet address of the group desired. Must not be NULL.

items  -  A list of specific items, separated by a null character, to be returned. Or, if all items are desired the caller may specify DIR_ITEMS_ALL_DOMINO. If NULL is specified then only the Notes DN is returned for each match in hCollection, and the number of matches are returned in numMatches. 
The order of the items in the list determines the index position that is specified in subsequent calls to DirEntryGetItem() in order to get the values of the items. 
Note that Domino ad hoc items must be asked for specifically. This is so that the existing buffer management code does not have to change significantly. For efficiency and speed this code depends on knowing all the items to be placed in the buffer when the first match is added. This is difficult or at least inefficient if there are multiple matches and the ad-hoc attributes differ between some/all the matches.

numItems  -  The number of items in the list of items to be returned. Specify 1 if one of the DIR_ITEMS_ values is specified. Specify 0 if items is NULL.

groupType  -  The Domino group type to limit the search to. One of: 
DIR_GROUP_TYPE_ANY - No specific group (all group types are a match) 
DIR_GROUP_TYPE_MULTIPURPOSE (default) - The group can be used anywhere. 
DIR_GROUP_TYPE_MAILONLY - The group cannot be used on ACLs or deny lists. 
DIR_GROUP_TYPE_ACCESSCONTROL - The group can only be used on ACLs. 
DIR_GROUP_TYPE_DENYLIST - The group can only be used on deny lists. 
DIR_GROUP_TYPE_SERVERONLY - The group can only be used for connection documents and to group server names.

Output :
(routine)  -  Status code: 
NOERROR on success. 
An ERR status on failure indicating the problem. 


hCollection  -  Handle to an allocated collection of entries that match the search criteria. If there are no matching entries, NOERROR will be returned and a non-NULL DIRCOLLECTION is returned in hCollection. 
Callers should not call DirEntryFree() on the returned directory entry objects! They will be indirectly freed by calling DirCollectionFree().

**See Also :**
[DirCtxSearchByName](D:/md_files/DirCtxSearchByName.md)
[DirCtxSearchDominoPersonsByName](D:/md_files/DirCtxSearchDominoPersonsByName.md)
[DirCtxSearchGroupsByName](D:/md_files/DirCtxSearchGroupsByName.md)
[DirCtxSearchPersonsByName](D:/md_files/DirCtxSearchPersonsByName.md)
---
