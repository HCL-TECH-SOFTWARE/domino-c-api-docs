##### Function : Folders
##### FolderRename - Renames a folder.
---
```
#include <foldman.h>
STATUS LNPUBLIC FolderRename(

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FolderNoteID,
	char far *pszName,
	WORD  wNameLen,
	DWORD  dwFlags);
```
**Description :**

This function renames the specified folder and its subfolders.

**Parameters :**
Input :
hDataDB  -  The handle to the open database where the folder to be renamed resides.

hFolderDB  -  Must be NULLHANDLE.

FolderNoteID  -  NOTEID of folder to be renamed.

pszName  -  New name for the folder.  Individual folder names are limited to DESIGN_FOLDER_MAX_NAME bytes.

wNameLen  -  Length of the pszName parameter.  If pszName is NULL terminated, you may use MAXWORD for this parameter.

dwFlags  -  Reserved for future use.  Specify  0L.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.



**See Also :**
[FolderCopy](/domino-c-api-docs/reference/Func/FolderCopy)
[FolderCreate](/domino-c-api-docs/reference/Func/FolderCreate)
[FolderDelete](/domino-c-api-docs/reference/Func/FolderDelete)
[FolderDocAdd](/domino-c-api-docs/reference/Func/FolderDocAdd)
[FolderDocCount](/domino-c-api-docs/reference/Func/FolderDocCount)
[FolderDocRemove](/domino-c-api-docs/reference/Func/FolderDocRemove)
[FolderDocRemoveAll](/domino-c-api-docs/reference/Func/FolderDocRemoveAll)
[FolderMove](/domino-c-api-docs/reference/Func/FolderMove)
---
