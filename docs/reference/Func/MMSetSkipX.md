##### Function : MIME
##### MMSetSkipX - set Conversion Controls 'skip X-Notes-Item headers' setting.
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetSkipX(

	CCHANDLE  hCC,
	BOOL  bSkipX);
```
**Description :**

The function  MMSetSkipX sets the Conversions Controls 'skip X-Notes-Item 
headers' setting to the input value, bSkipX.  No checking is done for out of 
bounds values.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

bSkipX  -  the value to use for the Conversion Controls 'skip X-Notes-Item headers' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetSkipX(hCC, TRUE); /* if TRUE, don't export any headers named x-notes-item 
(default FALSE) */
```
**See Also :**
[MMGetSkipX](/domino-c-api-docs/reference/Func/MMGetSkipX)
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
---
