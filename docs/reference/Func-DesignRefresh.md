##### Function : Database
##### DesignRefresh - Refresh a database design from a server's templates.
---
##### #include <design.h>
STATUS LNPUBLIC **DesignRefresh(**

	char *Server,
	DBHANDLE  hDB,
	DWORD  dwFlags,
	ABORTCHECKPROC  AbortCheck,
	OSSIGMSGPROC  MessageProc);
**Description :**
This function will refresh the database design, as allowed by the 
database/design properties and access control of Domino,  from a server's 
templates.  The refreshed database, if open in Domino or Notes at the time of 
refresh, must be closed and reopened to view any changes.
**Parameters :**
Input :
Server  -  A pointer to the null-terminated name of the Lotus Domino Server on which the database template resides.  The string should be no longer than MAXUSERNAME.  If you want to specify "no server" (the local machine), pass a pointer to "" (the null string).

hDB  -  Database handle of the file to be refreshed.

dwFlags  -  Options, please see DESIGN_xxx for possible values.  NOTE: If dwFlags is set to 0, the database will be refreshed the first time database design refresh is requested whether the Design Template has changed, the design of the database itself has been modified or no changes have been made.  Subsequent requests to refresh this same database, by calling the function DesignRefresh with dwFlags set to 0, will take place only if its Design Template has changed.

AbortCheck  -  Pointer to a user defined callback function that will check abort status.  NULL if none is desired.  See ABORTCHECKPROC.

MessageProc  -  Pointer to a user defined callback function that will handle the Message signal.  NULL if none is desired.  See OSSIGMSGPROC.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


**See Also :**
[ABORTCHECKPROC](D:/md_files/ABORTCHECKPROC.md)
[DESIGN_xxx](D:/md_files/DESIGN_xxx.md)
[OSSIGMSGPROC](D:/md_files/OSSIGMSGPROC.md)
---
