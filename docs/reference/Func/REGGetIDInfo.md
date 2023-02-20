##### Function : User Registration
##### REGGetIDInfo - Obtain information about an ID file
---
```
#include <reg.h>
STATUS LNPUBLIC REGGetIDInfo(

	char far *IDFileName,
	WORD  InfoType,
	void far *OutBufr,
	WORD  OutBufrLen,
	WORD far *ActualLen);
```
**Description :**

This function will obtain information about an ID contained in a file.  The 
information to be returned is specified by one of the REGIDGetxxx values passed 
as the second argument;  please refer to that reference entry.

If you specify REGGetIDInfo to return a public key, the public key is obtained 
from the id file.  This key is not the same as the certified public key stored 
in the Domino directory.  The certified public key includes the Public Key 
Certifier, the public key and the Certifier Type.

**Parameters :**
Input :
IDFileName  -  Pathname of the ID file to examine.

InfoType  -  One of the REGIDGetxxx values.  This value determines which information to retrieve;  the type of the returned data varies.

OutBufrLen  -  Size of the buffer.  If this value is less than the length of the data item, the error ERR_VALUE_LENGTH will be returned and the actual length of the item will be returned at *ActualLen.  If this value is greater than the length of the data item, the remainder of the buffer will be filled with 0.  It is recommended that a size of 560 bytes or more be supplied as the initial buffer size.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR  -  No error.
ERR_VALUE_LENGTH - The buffer space is insufficient for the value.  The actual length of the data is returned.
ERR_NOT_YET_IMPLEMENTED - The InfoType argument is not one of the supported values.
ERR_xxx  -  Various NSF, OS, and KFM errors.


OutBufr  -  Address where the information is to be placed.  If this value is NULL, the length of the item will be returned at *ActualLen.

ActualLen  -  Address where the number of bytes actually returned will be placed.  If this argument is NULL, the length information will not be returned.


**Sample Usage :**
```
STATUS      error;
BOOL        fIsCertifier;
char        nameBuffer [MAXUSERNAME];
WORD        actualLen;

error = REGGetIDInfo ("my.id", REGIDGetCertifierFlag, &fIsCertifier,
    sizeof (fIsCertifier), &actualLen);

error = REGGetIDInfo ("my.id", REGIDGetName, nameBuffer,
    MAXUSERNAME, &actualLen);

```
**See Also :**
[REGIDGetxxx](/reference/Symb/REGIDGetxxx)
---
