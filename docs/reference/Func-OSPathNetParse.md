##### Function : OS File
##### OSPathNetParse - Breaks pathname into port, server, and file names.
---
##### #include <osfile.h>
STATUS LNPUBLIC **OSPathNetParse(**

	const char far *PathName,
	char far *retPortName,
	char far *retServerName,
	char far *retFileName);
**Description :**
Given a fully-qualified network path specification to a Domino database file,  
this function breaks it into its port name, server name, and filename 
components.  If the fully-qualified path contains just the port name and/or 
server name components, then they will be the only ones returned.

You may obtain an expanded pathname by passing a valid DBHANDLE to 
NSFDbPathGet.  NSFDbPathGet returns the Expanded pathname of the open 
database.  You may then pass the expanded path name to OSPathNetParse to obtain 
the port name, server name and filename components.  You may use these 
components to construct a full path specification to a different Domino 
database on the same server, via the same port, simply by substituting a new 
filename in a call to OSPathNetConstruct.

Expanded database filepath syntax: 

{Port}   NetworkSeparator {servername}  ServerSuffix {filename}
COM1{NetworkSeparator}NOTESBETA{ServerSuffix}NOTEFILE\APICOMMS.NSF

Note:  the NetworkSeparator and ServerSuffix are not system independent.  To 
maintain the portability of your code, it is recommended that you make no 
explicit use of them anywhere in you programs.
**Parameters :**
Input :
PathName  -  A pointer to a text buffer containing the Expanded path specification of a Domino database file, stored as a null-terminated string.  The string will be broken into three components: Port name, Server name, and File path relative to the Domino or Notes data directory.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully parsed the given Expanded pathname into its component parts.
ERR_INV_SERVER_NAME - Portname or servername is invalid.  Also returned if a portname and filename are found without an intervening servername.
ERR_INV_FILE_NAME - File name is invalid.
ERR_xxx - Errors returned by lower level Notes functions: (memory management, file operations, etc.).  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


retPortName  -  Optional;  if not NULL, a pointer to the text buffer that receives the Port name component of the Expanded path as a null-terminated string or "" if there is none.

retServerName  -  Optional;  if not NULL, a pointer to the text buffer that receives the Server name component of the Expanded path as a null-terminated string or "" if there is none.

retFileName  -  Optional;  if not NULL, a pointer to the text buffer that receives the File name component of the Expanded path as a null-terminated string.  This will include any subdirectories relative to the Domino or Notes data directory.

**Sample Usage :**
```
/* Parse the fully qualified database pathname in to components*/

   if (error_status = OSPathNetParse(db_fullpath, port_name,
                                     server_name, file_name))
       goto Exit;
```
**See Also :**
[NSFDbOpen](D:/md_files/NSFDbOpen.md)
[NSFDbOpenExtended](D:/md_files/NSFDbOpenExtended.md)
[NSFDbPathGet](D:/md_files/NSFDbPathGet.md)
[OSPathNetConstruct](D:/md_files/OSPathNetConstruct.md)
---
