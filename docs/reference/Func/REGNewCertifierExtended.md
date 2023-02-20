##### Function : User Registration
##### REGNewCertifierExtended - Registers a new certifier.
---
```
#include <reg.h>
STATUS LNPUBLIC REGNewCertifierExtended(

	HCERTIFIER  hCertCtx,
	char far *RegServer,
	REG_CERTIFIER_INFO far *CertInfo,
	REGSIGNALPROC  signalstatus,
	char far *retErrorPathName,
	void far *Spare);
```
**Description :**

This function creates either an Organizational or Organizational Unit 
certifier.  

It performs three functions, each of which is separately selectable by setting 
the appropriate flag in the REGFlags member of REG_CERTIFIER_INFO:  
(1) Create a certifier's ID file and certify it if the certfier is of type 
ORGUNIT; 
(2) Create a mail file on the certifier's specified mail server; and 
(3) Add or modify the certifier record in the Domino Directory on the 
registration server.  

It will open the Domino Directory on the specified registration server, verify 
write access to the book, and look for the certifier specified by Org or 
OrgUnit.  If the certifier is found, an error will be returned unless the 
caller has specified in the REGFlags word that the certifier record may be 
modified.  If the ID file is found, an error will be returned unless the caller 
has specified that it may be modified (overwritten).

**Parameters :**
Input :
hCertCtx  -  Handle of a certifier context obtained by calling SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).  Use NULLHANDLE if creating an Organizational certifier.

RegServer  -  A pointer to the null-terminated name of the Lotus Domino registration server containing the Domino Directory.  The string should be no longer than MAXUSERNAME. If you want to specify "no server" (the local machine), pass a pointer to "" (the null string).

CertInfo  -  A pointer to a REG_CERTIFIER_INFO structure that has been initialized to zero, and has the Size and other data members populated.  Please see REG_CERTIFIER_INFO.

signalstatus  -  (Optional).  Pointer to a user defined procedure used to show status during registration.  See Data Type, Signal Handler section of this reference.  Otherwise use (REGSIGNALPROC) NULL for this parameter.

Spare  -  Reserved for future use.  Use NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR  -  No error.

ERR_REG_INC_CONTEXT  -  Non-optional fields are incomplete.

ERR_REG_ADDRBOOK_ENTRY_EXISTS  -  Flag not set to allow modification of existing certifier record.

ERR_REG_USERID_EXISTS  -  Flag not set to allow overwriting of an existing id.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


retErrorPathName  -  (Optional).  Pathname of file where file system error occurred.


**See Also :**
[REG_CERTIFIER_INFO](/reference/Data/REG_CERTIFIER_INFO)
[REG_ID_INFO](/reference/Data/REG_ID_INFO)
---
