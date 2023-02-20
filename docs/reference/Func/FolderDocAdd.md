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
[FolderCopy](/reference/Func/FolderCopy)
[FolderCreate](/reference/Func/FolderCreate)
[FolderDelete](/reference/Func/FolderDelete)
[FolderDocCount](/reference/Func/FolderDocCount)
[FolderDocRemove](/reference/Func/FolderDocRemove)
[FolderDocRemoveAll](/reference/Func/FolderDocRemoveAll)
[FolderMove](/reference/Func/FolderMove)
[FolderRename](/reference/Func/FolderRename)
---
