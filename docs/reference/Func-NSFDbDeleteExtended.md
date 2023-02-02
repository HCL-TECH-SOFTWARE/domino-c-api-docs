##### Function : Database
##### NSFDbDeleteExtended - Delete a database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbDeleteExtended(**

	cost char far *PathName,
	DHANDLE  hNameList);
**Description :**
This function deletes a specified Domino database using the path specification 
provided and allows for a NAMES_LIST structure UserName to provide 
authentication for trusted servers.
**Parameters :**
Input :
PathName  -  The address of a text buffer containing a database name or alternately, a full network path specification to the database built with OSPathNetConstruct.  The database file name should be a null-terminated string.

hNameList  -  May be NULLHANDLE or a HANDLE to a NAMES_LIST structure that contains a UserName that is used to provide authentication for trusted servers.  This causes the UserName's ACL permissions in the database to be enforced.  Please see NSFBuildNamesList for more information on building a NAMES_LIST structure.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - database successfully deleted.
ERR_NOACCESS - You are not authorized to perform that operation
ERR_NOEXIST -  File does not exist
ERR_DRIVE_NOT_READY - Drive is not ready
ERR_LOCK - File cannot be shared while in use by another process
ERR_IOERROR - I/O data error
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


**See Also :**
[NSFDbDelete](D:/md_files/NSFDbDelete.md)
[NSFDbOpen](D:/md_files/NSFDbOpen.md)
[NSFDbOpenExtended](D:/md_files/NSFDbOpenExtended.md)
[OSPathNetConstruct](D:/md_files/OSPathNetConstruct.md)
---
