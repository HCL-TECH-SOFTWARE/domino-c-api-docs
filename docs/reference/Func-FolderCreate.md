##### Function : Folders
##### FolderCreate - Creates new folder.
---
##### #include <foldman.h>
STATUS LNPUBLIC **FolderCreate(**

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FormatNoteID,
	DBHANDLE  hFormatDB,
	char far *pszName,
	WORD  wNameLen,
	DESIGN_TYPE  FolderType,
	DWORD  dwFlags,
	NOTEID far *pNoteID);
**Description :**
This function creates a new folder in the specified database.  If the user does 
not have create personal folders access for the database, then an error will be 
returned.
**Parameters :**
Input :
hDataDB  -  The handle to the open database where the new folder is to reside.  This database will also be used to obtain the new folder's design if the hFormatDB parameter is not specified.

hFolderDB  -  Must be NULLHANDLE.

FormatNoteID  -  Folder/view note with which to base the new folder's design.  Specify 0L to use the default design.  The default design is specified in an existing folder's design.  If there is no default design specified in an existing folder's design, then the default view note is used.

hFormatDB  -  The handle to the open database which contains the folder/view note with which to base the new folder's design.  You may specify NULLHANDLE if this is the same as hDataDb.

pszName  -  Name of new folder.  Individual folder names are limited to DESIGN_FOLDER_MAX_NAME bytes.  If this is to be a cascading folder (subfolder), use a backslash character to separate the folder names, for example, "Parent Folder\\New Folder".  In this example, New Folder will be a subfolder of Parent Folder.  If Parent Folder does not exist, it will be created.

wNameLen  -  Length of the pszName parameter.  If pszName is NULL terminated, you may use MAXWORD for this parameter.

FolderType  -  Folder type (DESIGN_TYPE_xxx).  Indicates whether folder is to be shared or private.

dwFlags  -  Reserved for future use.  Specify  0L.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.


pNoteID  -  Pointer to the returned NOTEID of the newly created folder.

**Sample Usage :**
```
error = FolderCreate (hDB2, NULLHANDLE, FormatNoteID, hDB1, 
                          "API Folder", MAXWORD,
                          DESIGN_TYPE_PRIVATE_DATABASE,
                          0L, &FNoteID);
```
**See Also :**
[FolderCopy](D:/md_files/FolderCopy.md)
[FolderDelete](D:/md_files/FolderDelete.md)
[FolderDocAdd](D:/md_files/FolderDocAdd.md)
[FolderDocCount](D:/md_files/FolderDocCount.md)
[FolderDocRemove](D:/md_files/FolderDocRemove.md)
[FolderDocRemoveAll](D:/md_files/FolderDocRemoveAll.md)
[FolderMove](D:/md_files/FolderMove.md)
[FolderRename](D:/md_files/FolderRename.md)
[DESIGN_TYPE_xxx](D:/md_files/DESIGN_TYPE_xxx.md)
---
