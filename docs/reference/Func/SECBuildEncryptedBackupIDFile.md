##### Function : Recovery
##### SECBuildEncryptedBackupIDFile - Create a backup copy of the ID file and return the respository name of where it should be mailed to.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECBuildEncryptedBackupIDFile(

	char *pIDFileName,
	KFM_PASSWORD *pCurrentPW,
	char *pBackupPath,
	char *retRepositoryBuf,
	DWORD  MaxRepositoryBufLen,
	DWORD *retRepositoryBufLen,
	void *pReserved,
	DWORD  ReservedFlags);
```
**Description :**

Given the name of the ID file,password and location of where to put a backup 
copy of the ID file, create the backup copy and return the respository 
information if requested.
Routine:
	1.Read in the KFC from the currently running ID file or from 
pIDFileName if non NULL
	2. Call SECKFMBuildEncryptedBackup
	3. If retRepositoryBuf is non NULL then fill in the repository name

**Parameters :**
Input :
pIDFileName  -  pointer to name of the ID file to be used to create a backup copy . NULL if use current

pCurrentPW  -  KFM_PASSWORD to pIDFileName - NULL if use current

pBackupPath  -  pointer to where the backup copy of the ID file will be created

retRepositoryBuf  -  pointer to receive the configured mail to address of the recovery information. (Optional) maybe NULL.

MaxRepositoryBufLen  -  max size of retRepositoryBuf

pReserved  -  reserved - should be set to NULL

ReservedFlags  -  reserved - should be set to 0

Output :
(routine)  -  NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


retRepositoryBufLen  -  the length value in retRepositoryBuf. (Optional) maybe NULL.


**Sample Usage :**
```
	 char   *puserIDPath = "D:\\sectester.id";
        char   *puserIDPass = "123456";
        char   *pUserIDBackUPPath = "d:\\sectesterBk.ide";
        char    strRepositoryBuf[MAXPATH];
        DWORD   repositoryBufRealLen = 0;

	// create a backup copy of the id file

	SECKFMCreatePassword(puserIDPass, &retHashedPassWD);

	if (err = SECBuildEncryptedBackupIDFile(puserIDPath, &retHashedPassWD, 
pUserIDBackUPPath,
	 strRepositoryBuf, MAXPATH, &repositoryBufRealLen, NULL, 0)) 
	{
	 fprintf(flog,"SECBuildEncryptedBackupIDFile failed\n");
	 printAPIErr(err);  
	 NotesTerm();
	}

See Sample Program :

MISC\IDBACKUP
```
**See Also :**
---
