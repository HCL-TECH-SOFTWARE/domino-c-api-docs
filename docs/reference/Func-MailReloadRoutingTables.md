##### Function : Mail Gateway
##### MailReloadRoutingTables - Reload routing tables from the Domino Directory (Server's Address book).
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailReloadRoutingTables(**

	DHANDLE  hTables,
	BOOL  EnableTrace,
	BOOL  EnableDebug,
	BOOL far *retAddressBookModified);
**Description :**
Refresh the in-memory routing tables from the  Domino Directory (Server's 
Address book).
**Parameters :**
Input :
hTables  -  Handle to the memory block containing the mail routing tables.

EnableTrace  -  If TRUE, tracing of mail routings is enabled.

EnableDebug  -  If TRUE, mail routing debug information is generated in the debugging log.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Routing tables loaded.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 


retAddressBookModified  -  TRUE if the  Domino Directory (Server's Address book) has been modified since the routing tables were loaded or refreshed.

**See Also :**
[MailLoadRoutingTables](D:/md_files/MailLoadRoutingTables.md)
[MailUnloadRoutingTables](D:/md_files/MailUnloadRoutingTables.md)
---
