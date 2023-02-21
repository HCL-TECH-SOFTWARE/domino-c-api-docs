##### Function : Folders
##### FolderDocAdd - Adds document(s) to a folder.
---
```
#include <foldman.h>
STATUS LNPUBLIC FolderDocAdd(

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FolderNoteID,
	DHANDLE  hTable,
	DWORD  dwFlags);
```
**Description :**

This function adds the document(s) specified in an ID Table from a folder.

**Parameters :**
Input :
hDataDB  -  The handle to the open database where the folder resides.

hFolderDB  -  Must be NULLHANDLE.

FolderNoteID  -  NOTEID of folder containing document(s) to be added.

hTable  -   Handle to the ID Table of document(s) to be added.

dwFlags  -  Reserved for future use.  Specify  0L.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.



**Sample Usage :**
```
/* To add documents to this folder, create an id table of docs */
  if (error = IDCreateTable(sizeof(NOTEID), &hIDTable))
  {
    NSFDbClose (hDB);
    API_RETURN (ERR(error));
  }
  if (error = IDInsert (hIDTable, Doc_ID, NULL))
  {
    IDDestroyTable (hIDTable);
    NSFDbClose (hDB);
    API_RETURN (ERR(error));
  }

  error = FolderDocAdd (hDB, NULLHANDLE, FNoteID, hIDTable, 0L);
  
```
**See Also :**
[FolderCopy](/domino-c-api-docs/reference/Func/FolderCopy)
[FolderCreate](/domino-c-api-docs/reference/Func/FolderCreate)
[FolderDelete](/domino-c-api-docs/reference/Func/FolderDelete)
[FolderDocCount](/domino-c-api-docs/reference/Func/FolderDocCount)
[FolderDocRemove](/domino-c-api-docs/reference/Func/FolderDocRemove)
[FolderDocRemoveAll](/domino-c-api-docs/reference/Func/FolderDocRemoveAll)
[FolderMove](/domino-c-api-docs/reference/Func/FolderMove)
[FolderRename](/domino-c-api-docs/reference/Func/FolderRename)
---
