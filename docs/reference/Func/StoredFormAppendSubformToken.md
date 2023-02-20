##### Function : Form
##### StoredFormAppendSubformToken - Add a token to the end of a subform name so that the subform won't be found in a pre 6 Client/Server
---
```
#include <dbmisc.h>
STATUS LNPUBLIC StoredFormAppendSubformToken(

	char*pszSubName,
	WORD  wSubNameBufferLen);
```
**Description :**

This function adds a token to the end of a subform name so that the subform 
won't be found in a pre 6 Client/Server.  (The 6 client and server will remove 
this token before looking up the subform name.)


**Parameters :**
Input :
pszSubName  -  a pointer to a buffer which contains the subform name

wSubNameBufferLen  -  a WORD containing the length of the text buffer

Output :
(routine)  -  Return STATUS from call.  NOERROR if successful.



**See Also :**
[StoredFormAddItems](/reference/Func/StoredFormAddItems)
[StoredFormRemoveItems](/reference/Func/StoredFormRemoveItems)
---
