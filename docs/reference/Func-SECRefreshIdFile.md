##### Function : Address Book
##### SECRefreshIdFile - Refresh an ID file.
---
##### #include <kfm.h>
STATUS LNPUBLIC **SECRefreshIdFile(**

	char *pIDFileName,
	char *pPassword,
	char *pServer,
	DWORD *retFlags,
	DWORD  Reserved,
	void *pReserved);
**Description :**
This routine will search the $USERS view of the name and address book 
(directory) on the specified server for the user name extracted out of the ID 
file.  If a unique match is found, then a check for Notes certificate changes, 
Internet certificate changes and user name changes is made.  If updates are 
allowed to be pulled into the ID file then they will be.  It will be up to the 
user to re-attach the ID file to where it is stored using either 
NSFNoteAttachFile or SECAttachIdFileToDB.
**Parameters :**
Input :
pIDFileName  -  Name of ID file to be refreshed with certificate and name changes.

pPassword  -  Password to the ID file to be refreshed.

pServer  -  Server whose name and address book (directory) is to be searched for user name, which was pulled from the ID file, for updates to Notes certificates, Internet certificates and name changes.

Reserved  -  Reserved, should be set to 0.

pReserved  -  Reserved, should be set to NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is.   The return codes include:

NOERROR - action successful


retFlags  -  Return flags indicating what has changed.  See SEC_refreshed_xxx.

**See Also :**
[SECAttachIdFileToDB](D:/md_files/SECAttachIdFileToDB.md)
[SECKFMClose](D:/md_files/SECKFMClose.md)
[SECKFMOpen](D:/md_files/SECKFMOpen.md)
[SEC_refreshed_xxx](D:/md_files/SEC_refreshed_xxx.md)
---
