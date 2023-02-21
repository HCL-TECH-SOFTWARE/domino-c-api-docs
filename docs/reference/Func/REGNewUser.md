##### Function : User Registration
##### REGNewUser - Registers a new user.
---
```
#include <reg.h>
STATUS LNPUBLIC REGNewUser(

	HCERTIFIER  hCertCtx,
	WORD  MakeIDType,
	char far *RegServer,
	REG_USERNAME_INFO far *RegUserNameInfo,
	REG_MAIL_INFO far *RegMailInfo,
	char far *Password,
	void far *pGroupList,
	char far *IDFileName,
	char far *Location,
	char far *Comment,
	char far *InternetAddress,
	char far *ProfileName,
	char far *LocalAdminName,
	REGFlags  Flags,
	REGFlagsExt  FlagsExt,
	WORD  MinPasswordLength,
	NOTEHANDLE far *phUserNote,
	DBHANDLE far *phUserNoteNAB,
	REGSIGNALPROC  signalstatus,
	char far *ErrorPathName,
	void far *Reserved,
	void far *Spare);
```
**Description :**

This function registers a new user.  It performs three functions, each of which 
can be selected separately by setting the appropriate flag in the REGFlags 
word:  (1)  Create and certify a user's ID file; (2)  Create a mail file on the 
user's specified mail server; and (3)  Add or modify the user's person record 
in the Domino Directory on the registration server.  It will open the Domino 
Directory on the specified registration server, verify write access to the 
book, and look for the EntryName specified.  If the user is found, an error 
will be returned unless the caller has specified in the REGFlags word that the 
user entry may be modified.  If the ID file is found, an error will be returned 
unless the caller has specified that it may be modified (overwritten).


**Parameters :**
Input :
hCertCtx  -  Handle of a certifier context obtained by calling SECKFMGetCertifierCtx (must be freed by a call to SECKFMFreeCertifierCtx).  You may specify NULLHANDLE if you do not specify the fREGCreateIDFileNow and you do specify a valid ID file for the IDFileName parameter.


MakeIDType  -  Must be one of:
KFM_IDFILE_TYPE_FLAT --  Flat name space (V2 compatible)
KFM_IDFILE_TYPE_STD  --   Standard (user/server hierarchical)
KFM_IDFILE_TYPE_DERIVED -- Derived from certifier context (ie:  non-hierarchical certifier context => FLAT, hierarchical certifier context =>STD).


RegServer  -  A pointer to the null-terminated name of the Lotus Domino registration server containing the Domino Directory.  The string should be no longer than MAXUSERNAME. If you want to specify "no server" (the local machine), pass a pointer to "" (the null string).


RegUserNameInfo  -  A pointer to the REG_USERNAME_INFO structure.  Please see REG_USERNAME_INFO.

RegMailInfo  -  A pointer to the REG_MAIL_INFO structure.  Please See REG_MAIL_INFO.

Password  -  (Optional).  The password for the new user (workstation).

pGroupList  -  (Optional).  A pointer to a list of groups to add the new user to, constructed with ListAllocate and ListAddEntries.  Specify NULL if the user is not to be added to any groups.

IDFileName  -  The pathname of the ID file for the new user (workstation).  If the fREGCreateIDFileNow flag is not specified, then this file must exist in order to create a mail file and/or add or modify the user's person record in the Domino Directory.  Specify NULL for this parameter to have the IDFile attached to the Person record in the N&A Book (attached file name defaults to UserID).


Location  -  (Optional).  The location of the workstation (used to help in identification if there is more than one with the same name).    Do not pass in a literal constant.

Comment  -  (Optional).  Any additional identifying information to be stored in the Address book or Domino Directory.


InternetAddress  -  A pointer to the internet address of the new user.

ProfileName  -  (Optional).  Setup profile name(s).

LocalAdminName  -  (Optional).  The name of the local administrator.

Flags  -  Flags that are set to specify options.  See Symbolic Value, fREGxxx, in this reference.

FlagsExt  -  Flags that are set to specify options.  See Symbolic Value, fREGExtxxx, in this reference.

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

phUserNote  -  Returns a pointer to the note handle of the new person document if the caller has specified the REGExtFlag fREGExtReturnPersonNote.  Please see fREGExtxxx.

phUserNoteNAB  -  Returns a handle to the user note in the NAB.

ErrorPathName  -  (Optional).  Pathname of file where file system error occurred.

Reserved  -  Reserved for future use.

Spare  -  Reserved for future use.


**Sample Usage :**
```
Message(ctx, "About to register User %s, db=%s, IDFile=%s\n", rUser.LastName, 
rMail.pMailFileName, szMailIDFile);

	do 
	{
	 error = REGNewUser(g->hCert,  /* handle to certifier context */
	     KFM_IDFILE_TYPE_DERIVED,
	     pServer,  /* server name */
	     &rUser,   /* User info */
	     &rMail,   /* Mail info */
	     pszPw,   /* password */
	     NULL,  
	     szMailIDFile, 
	     NULL, 
	     NULL,  
	     pszInet,  /* internet address */
	     NULL, 
	     NULL, 
	     rflags,
	     rflagsx,
	     0,   
	     &hUser,  /* handle to new user note */
	     &hNAB,  /* nab db handle */
	     NULL,  /* signal proc */
	     NULL,  
	     NULL, 
	     NULL); 

	 if (error)
	 {
	  Message(ctx, "ERROR: REGNewUser Failed for User %s (0x%x)--> %e\n", 
rUser.LastName, error, error); 
	  if (++nNumRetries <= nMaxRetries)
	   Message(ctx, "Retry (#%d) REGNewUser for User %s\n", nNumRetries, 
rUser.LastName); 
	 }
	 else
	 {
	  Message(ctx, "REGNewUser Successful for User %s\n", rUser.LastName); 
	  if (hUser)
	  { 
	  /* 
	   RegNewUser returned a NoteHandle to the Directory Document of the 
newly added user.
	   If the encryption option was selected, then update the Encryption 
field/item in the document.
	  */
	   if (bEncryptMail)
	   {
	    Message(ctx, "Setting '%s' item for User %s in Directory...\n", 
PERSON_ENCRYPT_INCOMING_MAIL, rUser.LastName);
	    error = NSFItemSetText(hUser, PERSON_ENCRYPT_INCOMING_MAIL, "1", 1);
	    if (error)
	    {
	     Message(ctx, "Error setting item '%s' in Person document for User 
%s (NSFItemSetText error: %e)\n", 
	          PERSON_ENCRYPT_INCOMING_MAIL, rUser.LastName, error);
	    }
	    else
	    {
	     error = NSFNoteUpdate(hUser, 0);
	     if (error)
	      Message(ctx, "Error updating Person document for User %s 
(NSFNoteUpdate error: %e)\n", 
	          rUser.LastName, error);
	    }
	   }
	   NSFNoteClose(hUser);
	   hUser = NULLHANDLE;
	  }
	  if (hNAB)
	  {
	   /* Handle to the Directory/NAB was returned by RegNewUSer, use it to 
close the NAB */
	   NSFDbClose(hNAB);
	   hNAB=NULLHANDLE;
	  }
	 }
	}
	while (error && (nNumRetries <= nMaxRetries));
```
**See Also :**
[fREGExtxxx](/domino-c-api-docs/reference/Symb/fREGExtxxx)
[fREGxxx](/domino-c-api-docs/reference/Symb/fREGxxx)
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[REGNewWorkstationExtended](/domino-c-api-docs/reference/Func/REGNewWorkstationExtended)
[REG_MAIL_INFO](/domino-c-api-docs/reference/Data/REG_MAIL_INFO)
[REG_USERNAME_INFO](/domino-c-api-docs/reference/Data/REG_USERNAME_INFO)
---
