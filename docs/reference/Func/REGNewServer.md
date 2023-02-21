##### Function : User Registration
##### REGNewServer - Registers a new server.
---
```
#include <reg.h>
STATUS LNPUBLIC REGNewServer(

	HCERTIFIER  hCertCtx,
	WORD  MakeIDType,
	char far *RegServer,
	char far *OrgUnit,
	char far *EntryName,
	char far *Password,
	char far *IDFileName,
	char far *Location,
	char far *Comment,
	char far *DomainName,
	char far *NetworkName,
	char far *AdminName,
	char far *ServerTitle,
	REGFlags  Flags,
	WORD  MinPasswordLength,
	REGSIGNALPROC  signalstatus,
	char far *ErrorPathName);
```
**Description :**

This function registers a new server.  It performs two functions, each of which 
is separately selectable by setting the appropriate flag in the REGFlags word:  
(1) Create and certify a server's ID file and (2) Add or modify the server 
record in the Domino Directory on the registration server.  It will open the 
Domino Directory on the specified registration server, verifying write access 
to the book, and look for the EntryName specified.  If the specified server is 
found, an error will be returned unless the caller has specified that the 
server entry may be modified.  If the ID file is found, an error will be 
returned unless the caller has specified that it may be modified (overwritten).

**Parameters :**
Input :
hCertCtx  -  Handle of a certifier context obtained from calling SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).    You may specify NULLHANDLE if you do not specify the fREGCreateIDFileNow and you do specify a valid ID file for the IDFileName parameter.

MakeIDType  -  One of:
	KFM_IDFILE_TYPE_FLAT - Flat name space (V2 compatible)
	KFM_IDFILE_TYPE_STD - Standard (server hierarchical)
	KFM_IDFILE_TYPE_DERIVED - Derived from certifier context, (non-hierarchical certifier context =>FLAT, hierarchical certifier context =>STD)

RegServer  -  A pointer to the null-terminated name of the Lotus Domino registration server containing the Domino Directory.  The string should be no longer than MAXUSERNAME. If you want to specify "no server" (the local machine), pass a pointer to "" (the null string).

OrgUnit  -  (Optional).  Organizational unit of the new server (hierarchical only and in addition to that derived from the certifier context).

EntryName  -  The name of the new server.

Password  -  (Optional).  The password for the new server.

IDFileName  -  The pathname of the ID file for the new server.   If the fREGCreateIDFileNow flag is not specified, then this file must exist in order to add or modify the server record in the Domino Directory.   Specify NULL for this parameter to have the IDFile attached to the Server record in the N&A Book (attached file name defaults to UserID).


Location  -  (Optional).  The location of the server (used to help in identification if there is more than one with the same name).  Do not pass in a literal constant.

Comment  -  (Optional).  Any additional identifying information to be stored in Domino Directory.

DomainName  -  The Notes domain of the new server.

NetworkName  -  (Optional).  The name of the network for the new server.   Do not pass in a literal constant.

AdminName  -  (Optional).  The name of the administrator for the new server.

ServerTitle  -  (Optional).  The server title to be stored in the Domino Directory.

Flags  -  Flags that are set to specify options.  See Symbolic Value, fREGxxx, in this reference.  Note that registration flags pertaining to the creation of a mail file  (fREGCreateMailFileNow and fRegCreateMailFileLocally) are not applicable to this function.

MinPasswordLength  -  Quality of password required for this server (0 - 16).

signalstatus  -  (Optional).  Pointer to a user defined procedure used to show status during registration.  See Data Type, Signal Handler section of this reference.  Otherwise use (REGSIGNALPROC) NULL for this parameter.

Output :
(routine)  -  Return status from this call - indicates either success or what the error is.  The return codes include:

NOERROR  -  No error.
ERR_REG_INC_CONTEXT  -  Non-optional fields are incomplete.  Depends on Flags used:
     fREGCreateIDFileNow requires MakeIDType, EntryName, IDFileName, and Password (if MinPasswordLength is not 0).
     fREGCreateAddrBookEntry requires EntryName.
ERR_REG_ADDRBOOK_ENTRY_EXISTS  -  Flag not set to allow modification of existing server record.
ERR_REG_USERID_EXISTS  -  Flag not set to allow overwriting of an existing server id.
ERR_xxx  -  Various NSF, OS, and KFM errors.


Location  -  Any run of white spaces in the input string will be replaced by a single space.

NetworkName  -  Any run of white spaces in the input string will be replaced by a single space.

ErrorPathName  -  (Optional).  Pathname of file where file system error occurred.


**Sample Usage :**
```
error = REGNewServer (
          hCertCtx,              /* certifier context */
          KFM_IDFILE_TYPE_DERIVED, /* derived from certifier context */
          ServName,              /* registration server */
          NULL,                  /* Org Unit - optional */
          NEW_SERVNAME,          /* name of this new server */
          "abcorp",              /* password */
          SERVER_ID,             /* ID file for new server */
          ServLocation,          /* location of server - optional */
          NULL,                  /* comment - optional*/
          DOMAIN_NAME,           /* Notes domain of new server */
          NULL,                  /* network name - optional */
          NEW_USERNAME,          /* administrator's name - optional */
          "Corporate Server",    /* server title */
          fREGCreateIDFileNow |  /* flags */
          fREGUSARequested    |
          fREGCreateAddrBookEntry,
          MIN_PASS_LEN,           /* minimum password length */
          REGCallback,            /* pointer to callback function */
          FullDBPath);            /* returned pathname of file where
                                     error occurred */
```
**See Also :**
[SECKFMGetCertifierCtx](/domino-c-api-docs/reference/Func/SECKFMGetCertifierCtx)
[SECKFMFreeCertifierCtx](/domino-c-api-docs/reference/Func/SECKFMFreeCertifierCtx)
[REGSIGNALPROC](/domino-c-api-docs/reference/Data/REGSIGNALPROC)
[fREGxxx](/domino-c-api-docs/reference/Symb/fREGxxx)
---
