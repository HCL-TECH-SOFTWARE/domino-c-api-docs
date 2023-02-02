##### Function : User
##### SECKFMGetUserName - Get current Username.
---
##### #include <kfm.h>
STATUS LNPUBLIC **SECKFMGetUserName(**

	char far *retUserName);
**Description :**
This function returns the Username associated with the workstation's or 
server's ID where this function is executed.  This function is equivalent to 
calling the function SECKFMUserInfo with the LICENSEID parameter set to NULL.
**Parameters :**

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - action successful


retUserName  -  The address of a text buffer in which a null-terminated user name string obtained from the local ID file is returned.   The buffer must have a minumum length of  MAXUSERNAME + 1 (see names.h). 

**Sample Usage :**
```

    char            szServer[MAXUSERNAME+1];

    if (error = SECKFMGetUserName (szServer))
    {
        printf ("Unable to get current server or user name.");
        return (error);
    }
```
**See Also :**
[SECKFMUserInfo](D:/md_files/SECKFMUserInfo.md)
---
