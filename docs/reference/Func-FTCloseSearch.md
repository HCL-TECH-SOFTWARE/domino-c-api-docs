##### Function : Full Text Search
##### FTCloseSearch - Closes an opened full text search handle.
---
##### #include <ft.h>
STATUS LNPUBLIC **FTCloseSearch(**

	DHANDLE  hSearch);
**Description :**
This function deallocates the memory associated with a full text search handle.
**Parameters :**
Input :
hSearch  -  Opened search handle.

Output :
(routine)  -   Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.


**See Also :**
[FTOpenSearch](D:/md_files/FTOpenSearch.md)
[FTSearch](D:/md_files/FTSearch.md)
---
