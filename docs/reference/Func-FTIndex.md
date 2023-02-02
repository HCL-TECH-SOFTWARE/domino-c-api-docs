##### Function : Full Text Search
##### FTIndex - Indexes a local database for full text searching capabilities.
---
##### #include <ft.h>
STATUS LNPUBLIC **FTIndex(**

	DBHANDLE  hDB,
	WORD  Options,
	char far *StopFile,
	FT_INDEX_STATS far *retStats);
**Description :**
This function creates a new full text index for a local database.  

Full text indexing of a remote database is not supported in the C API.
**Parameters :**
Input :
hDB  -  The handle to the open database.

Options  -  Indexing options.  See Symbolic Value, FT_INDEX_xxx.  These options may be or'd together.

StopFile  -  Domino and Notes R5 no longer use a Stop Word file.  Pass in NULL for this parameter.  In preveious releases of Domino and Notes, you could specify the name of the Stop Word file or pass in NULL for this parameter if there was no Stop Word file.  A Stop Word file contains words that were not to be indexed.  

Output :
(routine)  -    Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.


retStats  -  Pointer to returned indexing statistics.  Pass in NULL if no statistics are desired.

**See Also :**
[FT_INDEX_STATS](D:/md_files/FT_INDEX_STATS.md)
[FT_INDEX_xxx](D:/md_files/FT_INDEX_xxx.md)
---
