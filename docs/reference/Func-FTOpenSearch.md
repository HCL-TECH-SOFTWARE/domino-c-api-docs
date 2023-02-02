##### Function : Full Text Search
##### FTOpenSearch - Opens a full text search handle.
---
##### #include <ft.h>
STATUS LNPUBLIC **FTOpenSearch(**

	DHANDLE far *rethSearch);
**Description :**
This routine opens a full text search handle that is used in FTSearch.  After 
the search is completed, use FTCloseSearch to close the full text search handle 
and deallocate the memory associated with it.
**Parameters :**

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.


rethSearch  -  Pointer to returned search handle to be passed into FTSearch.  The returned handle could be zero.

**See Also :**
[FTCloseSearch](D:/md_files/FTCloseSearch.md)
[FTSearch](D:/md_files/FTSearch.md)
[FTSearchExt](D:/md_files/FTSearchExt.md)
---
