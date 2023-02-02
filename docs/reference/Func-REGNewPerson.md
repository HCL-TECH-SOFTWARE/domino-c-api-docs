##### Function : User Registration
##### REGNewPerson - Register a new person.
---
##### #include <reg.h>
STATUS LNPUBLIC **REGNewPerson(**

	HCERTIFIER  hCertCtx,
	char far *RegServer,
	REG_PERSON_INFO far *PersonInfo,
	REGSIGNALPROC  signalstatus,
	char far *RetErrorPathName,
	void far *Spare);
**Description :**
This function registers a new person.  

It performs four functions, each of which can be selected by setting the 
appropriate flags in the REGFlags, REGFlagsExt word members of 
REG_PERSON_INFO:  
(1)  Create and certify a person's ID file; 
(2)  Create a mail file on the person's specified mail server; 
(3)  Add or modify the person record in the Domino Directory on the 
registration server; and 
(4) Create roaming files on the person's specified roaming server.  

It will open the Domino Directory on the specified registration server, verify 
write access to the book, and look for the EntryName specified.  If the person 
is found, an error will be returned unless the caller has specified in the 
REGFlags word that the person record may be modified.  If the ID file is found, 
an error will be returned unless the caller has specified that it may be 
modified (overwritten).
**Parameters :**
Input :
hCertCtx  -  Handle of a certifier context obtained by calling SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).

RegServer  -  A pointer to the null-terminated name of the Lotus Domino registration server containing the Domino Directory.  The string should be no longer than MAXUSERNAME. If you want to specify "no server" (the local machine), pass a pointer to "" (the null string).

PersonInfo  -  A pointer to a REG_PERSON_INFO structure.  Please see REG_PERSON_INFO.

signalstatus  -  (Optional).  Pointer to a user defined procedure used to show status during registration.  See Data Type, Signal Handler section of this reference.  Otherwise use (REGSIGNALPROC) NULL for this parameter.

Spare  -  Reserved for future use.


Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR  -  No error.

ERR_REG_INC_CONTEXT  -  Non-optional fields are incomplete.

ERR_REG_ADDRBOOK_ENTRY_EXISTS  -  Flag not set to allow modification of existing person record.

ERR_REG_USERID_EXISTS  -  Flag not set to allow overwriting an existing person id.

ERR_REG_NO_MAILFILE_CREATED  -  Requested creation could not be done.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


RetErrorPathName  -  (Optional).  Pathname of file where file system error occurred.


**Sample Usage :**
```
error = REGNewPerson(hCertCtx, NULL,&UserInfo,SetupSignalStatus,
	  pErrorPath,
	  NULL);

	/* It's not fatal if "LocalDomainAdmins" could not be updated */
	if (error == ERR_REG_GROUPS_ERROR)
	 error = NOERROR;
```
**See Also :**
[REG_ID_INFO](D:/md_files/REG_ID_INFO.md)
[REG_MAIL_INFO_EXT](D:/md_files/REG_MAIL_INFO_EXT.md)
[REG_MISC_INFO](D:/md_files/REG_MISC_INFO.md)
[REG_PERSON_INFO](D:/md_files/REG_PERSON_INFO.md)
---
