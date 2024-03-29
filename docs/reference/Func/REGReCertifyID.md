##### Function : User Registration
##### REGReCertifyID - Re-certify the ID file.
---
```
#include <reg.h>
STATUS LNPUBLIC REGReCertifyID(

	HCERTIFIER  hCertCtx,
	WORD  Spare1,
	char far *RegServer,
	char far *OrgUnit,
	char far *IDFileName,
	TIMEDATE far *ExpirationTime,
	WORD  Spare2,
	VOID far *Spare3,
	REGSIGNALPROC  signalstatus,
	char far *ErrorPathName);
```
**Description :**

Re-certify the ID stored in an ID file.  Using this function, a new expiration 
date may be set for the ID, or the ID may be upgraded from flat to 
hierarchical.

**Parameters :**
Input :
hCertCtx  -  Handle of a certifier context obtained by calling SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).

Spare1  -  Reserved;  must be 0.

RegServer  -  A pointer to the null-terminated name of the Lotus Domino registration server containing the Domino Directory.  The string should be no longer than MAXUSERNAME. If you want to specify "no server" (the local machine), pass a pointer to "" (the null string).

OrgUnit  -  (Optional).  Organizational unit of the new user (hierarchical only and in addition to that derived from the certifier context).

IDFileName  -  The pathname of the ID file for the user.

ExpirationTime  -  New expiration time and date for the ID.

Spare2  -  Reserved;  must be 0.

Spare3  -  Reserved;  must be NULL.

signalstatus  -  (Optional).  Pointer to a user defined procedure used to show status during registration.  See Data Type, Signal Handler section of this reference.  Otherwise use (REGSIGNALPROC) NULL for this parameter.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR  -  No error.

ERR_xxx  -  Various NSF, OS, and KFM errors.


ErrorPathName  -  (Optional).  Pathname of file where file system error occurred.


**See Also :**
[REGSIGNALPROC](/domino-c-api-docs/reference/Data/REGSIGNALPROC)
---
