##### Function : Mail Gateway
##### MailLoadRoutingTablesExt - Load routing tables from the Domino Directory (Server's Address book) with additional options.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailLoadRoutingTablesExt(**

	DBHANDLE  hAddressBook,
	char far *LocalServersName,
	char far *LocalServersDomain,
	char far *LocalServersInternetDomain,
	char far *TaskName,
	BOOL  EnableTrace,
	BOOL  EnableDebug,
	DWORD  LoadFlags,
	DHANDLE far *rethTables);
**Description :**
Load the set of routing tables from the Domino Directory (Server's Address 
book) into memory.  The caller is responsible for freeing memory used for the 
routing tables by calling MailUnloadRoutingTables ().

This function is similar to MailLoadRoutingTables with the additional ability 
to specify the calling server's Internet domain name and the ability to specify 
a load flag.
**Parameters :**
Input :
hAddressBook  -  Handle to the open Domino Directory (Server's Address book).

LocalServersName  -  Null-terminated string containing the name of the local server - the server where this function call is taking place, in upper case.

LocalServersDomain  -  Null-terminated string containing the domain of the local server - the domain of the server where this function call is taking place.

LocalServersInternetDomain  -  Null-terminated string containing the Internet domain name of the local server - the Internet domain name of the server where this function call is taking place.

TaskName  -  Null-terminated string containing the name of the calling task.  This string uniquely identifies the different mail routing services on a given server.


EnableTrace  -  If TRUE, tracing of mail routings is enabled.

EnableDebug  -  If TRUE, mail routing debug information is generated in the debugging log.

LoadFlags  -  Optional.  See LOAD_xxx for possible values.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Routing tables loaded.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 


rethTables  -  Handle to the memory block containing the mail routing tables.  The caller must free this memory using MailUnloadRoutingTables ().

**See Also :**
[MailLoadRoutingTables](D:/md_files/MailLoadRoutingTables.md)
[MailUnloadRoutingTables](D:/md_files/MailUnloadRoutingTables.md)
[LOAD_xxx](D:/md_files/LOAD_xxx.md)
---
