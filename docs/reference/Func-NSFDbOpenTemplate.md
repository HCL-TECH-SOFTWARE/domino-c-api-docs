##### Function : Database
##### NSFDbOpenTemplate - Opens an existing Domino database or database template in either the private or shared data directory.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbOpenTemplate(**

	const char far *PathName,
	DBHANDLE far *rethDB);
**Description :**
This function takes a pathname to an existing Domino database or database 
template (whether on a Lotus Domino Server or a local database), opens the 
database, and returns a handle to it. All subsequent access to the database is 
carried out via this handle.  Use NSFDbClose to close the database file handle 
and deallocate the memory associated with it.

This function can also be used to open a directory. The resulting handle can be 
passed to NSFSearch to find the contents of the directory.  To open the local 
data directory, use OSGetEnvironmentString with the VariableName set to 
"Directory" to get the pathname of the local data directory or if NULL is 
specified, the local data directory (the value of the "Directory=" environment 
variable from notes.ini) will be opened.  

Because this function can open a directory or a database, do not use this 
function to test for the existence of a database. To test a handle to 
distinguish a database handle from a directory handle, use NSFDbModeGet. 
NSFDbModeGet takes a DBHANDLE as input and returns a pointer to a USHORT that 
specifies whether the handle is associated with a database or with a 
directory.  The USHORT values are defined in DB_xxx (NSFDbModeGet). 

This function differs from NSFDbOpen in that it will look for the database or 
database template both in the private data directory and the shared ("Common") 
data directory. Edit the notes.ini file and add the path to the "Common" 
directory to the variable SharedDataDirectory.  For example:

 SharedDataDirectory=C:\lotus\notes\common

**Parameters :**
Input :
PathName  -  A pointer to the pathname of a Domino template. The string must be null-terminated.

For a database: The directory part of the path may be omitted if the database is in the data directory.  The filename extension may be omitted if it is ".NSF" but NOT if it is a ".NTF" database template file extension.  If the database is on a remote server, a full network pathname must be built with OSPathNetConstruct.

For a directory: If the directory is local, simply use the pathname of the directory.   If NULL is specified, the local data directory (the value of the "Directory=" environment variable from notes.ini) will be opened.  If the directory is remote, build a network pathname with OSPathNetConstruct.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Template successfully opened.

ERR_NOT_NSF - File is not a template.

ERR_NSF_VERSION - Invalid NSF version.

ERR_BSAFE_USER_ABORT - User cancelled password dialog box.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 


rethDB  -  The address of a DBHANDLE in which a handle to the opened template is returned.  Use this handle for all subsequent access to the template.

**See Also :**
[NSFDbClose](D:/md_files/NSFDbClose.md)
[NSFDbCreate](D:/md_files/NSFDbCreate.md)
[NSFDbOpen](D:/md_files/NSFDbOpen.md)
[NSFDbOpenTemplateExtended](D:/md_files/NSFDbOpenTemplateExtended.md)
[OSPathNetConstruct](D:/md_files/OSPathNetConstruct.md)
[OSPathNetParse](D:/md_files/OSPathNetParse.md)
---
