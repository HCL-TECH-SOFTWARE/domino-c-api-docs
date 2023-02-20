##### Function : User
##### SECKFMGetPublicKey - Get the certified public key for a  user.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECKFMGetPublicKey(

	char far *pName,
	WORD  Function,
	WORD  Flags,
	DHANDLE far *rethPubKey);
```
**Description :**

Retrieve the certified public key for a given user name from the Address book 
or from the Domino directory.  The function code is used to specify whether to 
retrieve the certified public key for primary or international encryption.  The 
certified public key is placed in a memory object allocated by Domino or 
Notes;  the application is responsible for freeing this memory object.

The certified public key includes the Public Key Certifier, the public key and 
the Certifier Type.  If you just want to retrieve the public key that is stored 
in the user's id file, use REGGetIDInfo.

**Parameters :**
Input :
pName  -  Pointer to the null-terminated user name.

Function  -  Function code specifying which public key to retrieve;  must be one of the KFM_pubkey_xxx values.

Flags  -  Reserved;  must be 0.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - action successful
ERR_USER_NOT_FOUND - cannot find an Address book entry or Domino Directory (Server's Address book) entry for that name.


rethPubKey  -  The handle to the memory object containing the public key is stored at this address.


**See Also :**
[KFM_pubkey_xxx](/reference/Symb/KFM_pubkey_xxx)
[REGGetIDInfo](/reference/Func/REGGetIDInfo)
---
