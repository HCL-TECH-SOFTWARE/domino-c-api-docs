##### Function : MIME
##### MMSetKeepTabs - set Conversion Controls 'keep tabs' setting.
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetKeepTabs(

	CCHANDLE  hCC,
	BOOL  bKeepTabs);
```
**Description :**

The function  MMSetKeepTabs sets the Conversions Controls 'keep tabs' setting 
to the input value, bKeepTabs.  No checking is done for out of bounds values.


**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

bKeepTabs  -  the value to use for the Conversion Controls 'keep tabs' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetKeepTabs(hCC, FALSE); /* if TRUE, when converting CD to MIME, don't 
convert tabs to spaces (default is FALSE) */
```
**See Also :**
[MMGetKeepTabs](/domino-c-api-docs/reference/Func/MMGetKeepTabs)
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
---
