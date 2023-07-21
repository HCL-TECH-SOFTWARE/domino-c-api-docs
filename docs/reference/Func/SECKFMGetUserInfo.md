##### Function : ID
##### SECKFMGetUserInfo - Get user access information for given key file.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECKFMGetUserInfo(

	KFHANDLE  hKFC,
	char far *lpName,
	LICENSEID far *lpLicense);
```

**Description :**

<font size="4">This routine retrieves access information of User name and LICENSEID associated with a key file context. As this API returns user name &amp; license information based on the ID file handle populated using </font><font size="4" face="Courier New">SECKFMOpen</font><font size="4">().  </font><br>
<font size="4">  </font><font size="4">User name buffer must have a minimum length of  MAXUSERNAME + 1 (see names.h for MAXUSERNAME) &amp; may be NULL, if you do not wish this string to be returned.</font><br>
<font size="4">  Refer LICENSEID structure information from global.h.</font>


**Parameters :**
Input :
hKFC  -  keyfile context to be used for access 

Output :
(routine)  -  NOERROR - on success.
   Notes error - on failure to get user and license ID.


lpName  -  The address of a text buffer in which a null-terminated user name string obtained from the local ID file is returned. 

lpLicense  -  The address of a LICENSEID structure in which the LICENSEID obtained from the local ID file is returned. This argument may be NULL if you do not wish this structure to be returned. 



**Sample Usage :**
```
char szUserName[MAXUSERNAME] = { 0 };
LICENSEID licenseID = { 0 };
KFHANDLE hKFC = NULLHANDLE;

SECKFMOpen(hKFC,
           idFilePath,         //Is the path to the ID file
           passwordBuffer,     // Password buffer
           0,
           0,
           NULL);
STATUS sStatus = SECKFMGetUserInfo(hKFC, szUserName, &licenseID);
if (NOERROR != sStatus)
{
    printf("ERROR TRACE: SECKFMGetUserInfo()");
    return sStatus;
}
printf("SECKFMGetUserInfo returned username %s.\n", szUserName);
SECKFMClose(&hKFC,
            0,
            0,
            NULL);
```

**See Also :**
[SECKFMGetIDFlags](/domino-c-api-docs/reference/Func/SECKFMGetIDFlags)
[SECKFMClose](/domino-c-api-docs/reference/Func/SECKFMClose)
[SECKFMOpen](/domino-c-api-docs/reference/Func/SECKFMOpen)
---
