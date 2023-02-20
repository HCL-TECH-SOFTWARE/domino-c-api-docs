##### Function : User Registration
##### REGNewServerExtended2 - Registers a new server.
---
```
#include <reg.h>
STATUS LNPUBLIC REGNewServerExtended2(

	HCERTIFIER  hCertCtx,
	char far *RegServer,
	REG_SERVER_INFO far *CertInfo,
	REGSIGNALPROC  signalstatus,
	char far *retErrorPathName,
	void far *Spare);
```
**Description :**

This function registers a new server.  

It performs two functions, each of which is separately selectable by setting 
the appropriate flag in the REGFlags member of REG_SERVER_INFO:  
(1) Create and certify a server's ID file and 
(2) Add or modify the server record in the Domino Directory on the registration 
server.  

It will open the Domino Directory on the specified registration server, 
verifying write access to the book, and look for the EntryName specified.  If 
the specified server is found, an error will be returned unless the caller has 
specified that the server entry may be modified.  If the ID file is found, an 
error will be returned unless the caller has specified that it may be modified 
(overwritten).

**Parameters :**
Input :
hCertCtx  -  Handle of a certifier context obtained by calling SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).

RegServer  -  A pointer to the null-terminated name of the Lotus Domino registration server containing the Domino Directory.  The string should be no longer than MAXUSERNAME. If you want to specify "no server" (the local machine), pass a pointer to "" (the null string).

CertInfo  -  A pointer to a REG_SERVER_INFO structure.  Please see REG_SERVER_INFO.

signalstatus  -  (Optional).  Pointer to a user defined procedure used to show status during registration.  See Data Type, Signal Handler section of this reference.  Otherwise use (REGSIGNALPROC) NULL for this parameter.

Spare  -  Reserved for future use.  Use NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR  -  No error.

ERR_REG_INC_CONTEXT  -  Non-optional fields are incomplete.  

ERR_REG_ADDRBOOK_ENTRY_EXISTS  -  Flag not set to allow modification of existing server record.

ERR_REG_USERID_EXISTS  -  Flag not set to allow overwriting of an existing server id.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


retErrorPathName  -  (Optional).  Pathname of file where file system error occurred.


**See Also :**
[REG_ID_INFO](/reference/Data/REG_ID_INFO)
[REG_MISC_INFO](/reference/Data/REG_MISC_INFO)
[REG_SERVER_INFO](/reference/Data/REG_SERVER_INFO)
---
