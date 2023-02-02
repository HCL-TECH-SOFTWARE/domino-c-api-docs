##### Function : User Registration
##### REGCrossCertifyID - Cross-certify an ID by a different organization
---
##### #include <reg.h>
STATUS LNPUBLIC **REGCrossCertifyID(**

	HCERTIFIER  hCertCtx,
	WORD  Spare1,
	char far *RegServer,
	char far *IDFileName,
	char far *Location,
	char far *Comment,
	char far *ForwardAddress,
	WORD  Spare2,
	REGSIGNALPROC  pStatusFunc,
	char far *ErrorPathName);
**Description :**
This function will cross-certify an ID with another organization's hierarchy.  
It will open the Domino Directory (Server's Address book) on the specified 
registration server, verify write access to the book, and add a new Cross 
Certificate entry.
**Parameters :**
Input :
hCertCtx  -  Handle of a certifier context obtained by calling SECKFMGetCertfierCtx (must be freed by a call to SECKFMFreeCertifierCtx).

Spare1  -  Reserved;  must be 0.

RegServer  -  A pointer to the null-terminated name of the Lotus Domino registration server containing the Domino Directory.  The string should be no longer than MAXUSERNAME. If you want to specify "no server" (the local machine), pass a pointer to "" (the null string).

IDFileName  -  Required:  the pathname of the ID file to be cross-certified.

Location  -  Optional;  not currently used.

Comment  -  Optional.  Any additional identifying information to be stored in the Domino Directory.

ForwardAddress  -  Optional;  not currently used.

Spare2  -  Reserved;  must be 0.

pStatusFunc  -  Optional.  Pointer to a user defined procedure used to show status during registration.  See Data Type, Signal Handler section of this reference.  Otherwise use (REGSIGNALPROC) NULL for this parameter.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR  -  No error.
ERR_xxx  -  Various NSF, OS, and KFM errors.


ErrorPathName  -  Optional.  Pathname of file where file system error occurred.

**Sample Usage :**
```
error= REGCrossCertifyID(hKfmCertCtx,0,szRegServer,pCertie->path,NULL,NULL,
	 NULL,0,NULL,ErrorPathName);
	SECKFMFreeCertifierCtx(hKfmCertCtx);
	if (error)  
	 goto err_exit;
```
**See Also :**
[SECKFMGetCertifierCtx](D:/md_files/SECKFMGetCertifierCtx.md)
[SECKFMFreeCertifierCtx](D:/md_files/SECKFMFreeCertifierCtx.md)
[REGSIGNALPROC](D:/md_files/REGSIGNALPROC.md)
---
