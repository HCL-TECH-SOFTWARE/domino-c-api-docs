##### Function : Mail Gateway
##### MailOpenMessageFile - Opens a gateway's outbound message file.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailOpenMessageFile(**

	char far *FileName,
	DBHANDLE far *rethFile);
**Description :**
This functions opens a gateway's outbound message file. 

A handle to a message file is equivalent to an NSF database handle and can be 
used, if needed, in direct NSF calls.  Use MailCloseMessageFile to close the 
message file handle and deallocate the memory associated with it.
**Parameters :**
Input :
FileName  -  Message file pathname string pointer (null-terminated).  May be NULL which will default to the mail.box file on the Lotus Domino Server.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


rethFile  -  Message file handle.

**Sample Usage :**
```
 STATUS      error = NOERROR;
    char       *szServerName;
    char       *szMailFile;
    char        szMailFilePath[MAXPATH+1];
    HANDLE      hMessageFile;
 
    szServerName = argv[1];
    szMailFile = argv[2];

    OSPathNetConstruct( NULL,               /* port name  */
                        szServerName,   
                        szMailFile,
                        szMailFilePath);

    /* Open the message file. */

    if (error = MailOpenMessageFile(szMailFilePath, &hMessageFile))
    {
        printf ("Error: unable to open '%s'.\n", szMailFilePath);
        goto Exit0;
    }
```
**See Also :**
[MailCloseMessageFile](D:/md_files/MailCloseMessageFile.md)
---
