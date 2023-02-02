##### Function : OS File
##### OSPathNetConstruct - Given port, server, and filename, create full path.
---
##### #include <osfile.h>
STATUS LNPUBLIC **OSPathNetConstruct(**

	const char far *PortName,
	const char far *ServerName,
	const char far *FileName,
	char far *retPathName);
**Description :**
This function takes a port name, a server name, and file path relative to the 
Domino or Notes data directory and creates a full network path specification 
for a Domino database file.

To open a Domino database on a server, use this function to create the full 
path specification, and pass this specification as input to NSFDbOpen or 
NSFDbOpenExtended.
**Parameters :**
Input :
PortName  -  A pointer to a text buffer containing the network port name as a null-terminated string.  Specify NULL to allow Domino or Notes to use the "most available" port to the given server.

ServerName  -  A pointer to the null-terminated name of the Lotus Domino Server you wish to access.  Information on servers is available from the Domino Directory (Server's Address book) using standard NIF and NSF APIs.  The string should be no longer than MAXUSERNAME. If you want to specify "no server" (the local machine), pass a pointer to "" (the null string).

The server name may be specified as the fully qualified hierarchical name (such as CN=ServerC/OU=Operations/O=Acme), the abbreviated hierarchical name (such as ServerC/Operations/Acme), or by the common name (such as ServerC).

FileName  -  A pointer to the filename of the Domino database you wish to access as a null-terminated string.  The filename should be "relative" to the Domino or Notes data directory on the server or workstation (fully specified pathnames, including drive letters, cannot be supplied to a Lotus Domino Server for security reasons).  Information on which databases are available on a particular server is available from the Domino Database Catalog, using standard NIF and NSF APIs.  The string should be no longer than MAXPATH.

If you use "" (the null string) for this parameter, then the default data directory will be specified.

Output :
(routine)  -  Always returns NOERROR.


retPathName  -  A pointer to the text buffer that will receive the fully qualified network path as a null-terminated string.  It should be dimensioned with MAXPATH and in the case where the fully qualified network path exceeds MAXPATH, the return string will be truncated at (MAXPATH - 1) and a NULL terminator will be added to the end.

**Sample Usage :**
```

/* Construct fully qualified path from components */

if (strlen(server_name))
{
    if (error_status = OSPathNetConstruct(NULL, server_name,
                                       file_name, fullpath_name))
        goto Exit;
}
else
    strcpy(fullpath_name, file_name);
    
if (error_status = NSFDbOpen(fullpath_name, &db_handle))
   goto Exit;

```
**See Also :**
[OSPathNetParse](D:/md_files/OSPathNetParse.md)
[NSFDbPathGet](D:/md_files/NSFDbPathGet.md)
[NSFDbOpen](D:/md_files/NSFDbOpen.md)
---
