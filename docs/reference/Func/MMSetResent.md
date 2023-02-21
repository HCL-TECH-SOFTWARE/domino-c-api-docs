##### Function : MIME
##### MMSetResent - set Conversion Controls 'support resent headers' setting.
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetResent(

	CCHANDLE  hCC,
	BOOL  bSupportResent);
```
**Description :**

The function  MMSetResent sets the Conversions Controls 'support resent 
headers' setting to the input value, bSupportResent.  No checking is done for 
out of bounds values.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

bSupportResent  -  the value to use for the Conversion Controls 'support resent headers' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetResent(hCC, FALSE); /* if TRUE support Resent-XXX headers when importing 
(default is FALSE) */
```
**See Also :**
[MMGetResent](/domino-c-api-docs/reference/Func/MMGetResent)
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
---
