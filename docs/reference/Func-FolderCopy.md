##### Function : Folders
##### FolderCopy - Copies a folder.
---
##### #include <foldman.h>
STATUS LNPUBLIC **FolderCopy(**

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FolderNoteID,
	char far *pszName,
	WORD  wNameLen,
	DWORD  dwFlags,
	NOTEID far *pNewNoteID);
**Description :**
This function creates a new folder and copies the contents of the source folder 
to it.  Any subfolders are also copied.
**Parameters :**
Input :
hDataDB  -  The handle to the open database where the source folder resides and where the new copy of the folder will reside.  

hFolderDB  -  Must be NULLHANDLE

FolderNoteID  -  NOTEID of source folder.

pszName  -  Name for the new copy of the folder.  Individual folder names are limited to DESIGN_FOLDER_MAX_NAME bytes.  If this is to be a cascading folder (a subfolder), use a backslash character to separate the folder names, for example, "Parent Folder\\New Copy"  In this example, New Copy will be a subfolder of Parent Folder.  If Parent Folder does not exist, it will be created.

wNameLen  -  Length of the pszName parameter.  If pszName is NULL terminated, you may use MAXWORD for this parameter.

dwFlags  -  Reserved for future use.  Specify  0L.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.


pNewNoteID  -  Pointer to the returned NOTEID of the new copy of the folder.  You may use NULL for this parameter if you do not require this information.  If the source folder contains subfolders, the NOTEID returned is the last subfolder that is copied.

**Sample Usage :**
```
error = FolderCopy (hDB, NULLHANDLE, FolderNoteID, "New Folder", MAXWORD, 0L, 
pNewNoteID);
```
**See Also :**
[FolderCreate](D:/md_files/FolderCreate.md)
[FolderDelete](D:/md_files/FolderDelete.md)
[FolderDocAdd](D:/md_files/FolderDocAdd.md)
[FolderDocCount](D:/md_files/FolderDocCount.md)
[FolderDocRemove](D:/md_files/FolderDocRemove.md)
[FolderDocRemoveAll](D:/md_files/FolderDocRemoveAll.md)
[FolderMove](D:/md_files/FolderMove.md)
[FolderRename](D:/md_files/FolderRename.md)
---
