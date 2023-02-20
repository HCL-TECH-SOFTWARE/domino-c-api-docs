##### Function : User Registration
##### REGNewWorkstation - Registers a new workstation.
---
```
#include <reg.h>
STATUS LNPUBLIC REGNewWorkstation(

	HCERTIFIER  hCertCtx,
	WORD  MakeIDType,
	char far *RegServer,
	char far *OrgUnit,
	char far *LastName,
	char far *FirstName,
	char far *MidInitial,
	char far *Password,
	char far *IDFileName,
	char far *Location,
	char far *Comment,
	WORD  MailSystem,
	char far *MailServerName,
	char far *MailFileName,
	char far *ForwardAddress,
	REGFlags  Flags,
	WORD  MinPasswordLength,
	REGSIGNALPROC  signalstatus,
	char far *ErrorPathName);
```
**Description :**

This function registers a new workstation.  It performs three functions, each 
of which can be selected separately by setting the appropriate flag in the 
REGFlags word:  (1)  Create and certify a user's ID file; (2)  Create a mail 
file on the user's specified mail server; and (3)  Add or modify the user's 
person record in the Domino Directory on the registration server.  It will open 
the Domino Directory on the specified registration server, verify write access 
to the book, and look for the EntryName specified.  If the user is found, an 
error will be returned unless the caller has specified in the REGFlags word 
that the user entry may be modified.  If the ID file is found, an error will be 
returned unless the caller has specified that it may be modified (overwritten).

**Parameters :**
Input :
hCertCtx  -  Handle of a certifier context obtained by calling SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).  You may specify NULLHANDLE if you do not specify the fREGCreateIDFileNow and you do specify a valid ID file for the IDFileName parameter.

MakeIDType  -  Must be one of:
KFM_IDFILE_TYPE_FLAT --  Flat name space (V2 compatible)
KFM_IDFILE_TYPE_STD  --   Standard (user/server hierarchical)
KFM_IDFILE_TYPE_DERIVED -- Derived from certifier context (ie:  non-hierarchical certifier context => FLAT, hierarchical certifier context =>STD).

RegServer  -  A pointer to the null-terminated name of the Lotus Domino registration server containing the Domino Directory.  The string should be no longer than MAXUSERNAME. If you want to specify "no server" (the local machine), pass a pointer to "" (the null string).

OrgUnit  -  (Optional).  Organizational unit of the new user (hierarchical only and in addition to that derived from the certifier context).

LastName  -  The last name of the new user (workstation).

FirstName  -  (Optional).  The first name of the new user (workstation).  Do not specify NULL for this parameter.  If no first name is to be used, specify, "" (the null string), for this parameter.

MidInitial  -  (Optional).  The middle initial of the new user (workstation).

Password  -  (Optional).  The password for the new user (workstation).

IDFileName  -  The pathname of the ID file for the new user (workstation).  If the fREGCreateIDFileNow flag is not specified, then this file must exist in order to create a mail file and/or add or modify the user's person record in the Domino Directory.  Specify NULL for this parameter to have the IDFile attached to the Person record in the Domino Directory (attached file name defaults to UserID).

Location  -  (Optional).  The location of the workstation (used to help in identification if there is more than one with the same name).  Do not pass in a literal constant.

Comment  -  (Optional).  Any additional identifying information to be stored in the Domino Directory.

MailSystem  -  (Optional).  Defaults to Notes mail user.  One of:
MAILSYSTEM_NOTES - Notes mail user
MAILSYSTEM_CCMAIL - CC:mail user
MAILSYSTEM_VIMMAIL - VIM compatible mail user
MAILSYSTEM_NONE - no mail system

MailServerName  -  (Optional).  Name of the server where the workstation's mailfile will reside.  If you want to create the mailfile on the local system, specify the user name associated with the workstation for this parameter.  Use SECKFMGetUserName() to get the user name.  You must also specify the fREGCreateMailFileNow in the flags parameter to create the mailfile.

MailFileName  -  (Optional;  required if the flag fREGCreateMailFileNow is specified).  The pathname of the mailfile.

ForwardAddress  -  (Optional).  Another Notes domain or foreign mail gateway where mail is to be forwarded.

Flags  -  Flags that are set to specify options.  See Symbolic Value, fREGxxx, in this reference.

MinPasswordLength  -  Quality of password required for this user (0 - 16)

signalstatus  -  (Optional).  Pointer to a user defined procedure used to show status during registration.  See Data Type, Signal Handler section of this reference.  Otherwise use (REGSIGNALPROC) NULL for this parameter.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR  -  No error.
ERR_REG_INC_CONTEXT  -  Non-optional fields are incomplete.  Depends on Flags used:
     fREGCreateIDFileNow requires MakeIDType (defaults to DERIVED if invalid), LastName, IDFileName, and Password (if MinPasswordLength is not 0).
     fREGCreateMailFileNow requires LastName, MailServerName, and MailFileName.
     fREGCreateAddrBookEntry requires LastName.
ERR_REG_ADDRBOOK_ENTRY_EXISTS  -  Flag not set to allow modification of existing user record.
ERR_REG_USERID_EXISTS  -  Flag not set to allow overwriting an existing user id.
ERR_REG_NO_MAILFILE_CREATED  -  Requested creation could not be done.
ERR_xxx  -  Various NSF, OS, and KFM errors.


Location  -  Any run of white spaces in the input string will be replaced by a single space.

ErrorPathName  -  (Optional).  Pathname of file where file system error occurred.


**Sample Usage :**
```
/* Prepare to call REGNewWorkstation() to create and register a new 
  user. First get the Organization Unit Certifier context for ABCorp,
  Sales Unit. Then, pass this certifier context as input to 
  REGNewWorkstation(). It will certify the new user with this 
  certifier. 
*/
if (error = GetCertCtx(ORGUNIT_CERT_ID, &hCertCtx, "abcorp"))
{
    return (ERR(error));
}
   
error = REGNewWorkstation (
      hCertCtx,              /* certifier context */
      KFM_IDFILE_TYPE_DERIVED, /* derived from certifier context */
      ServName,              /* Registration server */
      "Inside Sales",        /* Org Unit - provides uniqueness
                                to the name */
      "Doe",                 /* Last name */
      "Jayne",               /* First name */
      NULL,                  /* no middle initial */
      NULL,                  /* no password initially */
      USER_ID,               /* ID file name */
      WorkLocation,          /* location - optional */
      NULL,                  /* comment - optional */
      MAILSYSTEM_NOTES,             /* mail system  */
      ServName,              /* mail server name */
      MAILFILENAME,          /* pathname of mail file */
      NULL,                  /* forward address - optional */
      fREGCreateIDFileNow |  /* flags */
      fREGUSARequested    |
      fREGCreateMailFileNow |
      fREGCreateAddrBookEntry,
      0,                      /* minimum password length */
      REGCallback,            /* pointer to callback function */
      FullDBPath);            /* returned pathname of file where
                                 error occurred */
```
**See Also :**
[SECKFMGetCertifierCtx](/reference/Func/SECKFMGetCertifierCtx)
[SECKFMFreeCertifierCtx](/reference/Func/SECKFMFreeCertifierCtx)
[REGSIGNALPROC](/reference/Data/REGSIGNALPROC)
[fREGxxx](/reference/Symb/fREGxxx)
---
