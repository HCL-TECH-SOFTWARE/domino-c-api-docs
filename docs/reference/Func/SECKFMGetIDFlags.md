##### Function : ID
##### SECKFMGetIDFlags - Get ID flags information associated to keyfile context.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECKFMGetIDFlags(

	KFHANDLE  hKFC,
	WORD *pWFlags);
```

**Description :**

<font size="4">This routine provides access to ID flags associated with the keyfile context that is passed in. This API can return below flags,</font><br>
<font color="#121212" face="Courier New">fIDFH_Password   </font><font size="4"> </font><font color="#121212" face="Courier New">0x0001 </font><font size="4"> which indicates that file is password protected.</font><br>
<font color="#121212" face="Courier New">fIDFH_PWShareable   0x0008</font><font size="4">          which indicates that password may be shared by all process.</font><br>
<font size="4">Information on these flags can be seen in kmf.h file.</font>


**Parameters :**
Input :
hKFC  -  keyfile context to be used for access.

Output :
(routine)  -  NOERROR - on success.
  Notes Error - on fail to reterive ID flags.


pWFlags  -  Pointer to WORD which will receive the ID flags. 



**Sample Usage :**
```
#include <kfm.h>
KFHANDLE hKFC = NULLHANDLE;
WORD wFlags = 0;
/* Open ID file and populate hKFC handle */

STATUS sStatus = SECKFMGetIDFlags(hKFC, &wFlags);

if (NOERROR != sStatus)
{
    printf("Error in SECKFMGetIDFlags call");
    return sStatus;
}
printf("SECKFMGetIDFlags returned ID flags %d.\n", wFlags);
if (fIDFH_Password & wFlags)
{
    printf("SECKFMGetIDFlags returned ID as password protected.\n");
    wFlags &= ~fIDFH_Password;
}
if (!(fIDFH_PWShareable & wFlags))
{
     printf("SECKFMGetIDFlags returned ID as not shareable with other 
processes.\n");
}
else
{
    printf("SECKFMGetIDFlags returned ID as shareable with other processes.\n");
    wFlags &= ~fIDFH_PWShareable;
}
```

**See Also :**
[SECKFMGetUserInfo](/domino-c-api-docs/reference/Func/SECKFMGetUserInfo)
[SECKFMClose](/domino-c-api-docs/reference/Func/SECKFMClose)
[SECKFMOpen](/domino-c-api-docs/reference/Func/SECKFMOpen)
---
