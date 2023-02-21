##### Function : MIME
##### MMSetAddPhrase - set Conversion Controls 'add phrase' setting.
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetAddPhrase(

	CCHANDLE  hCC,
	WORD  wAddPhrase);
```
**Description :**

The function  MMSetAddPhrase sets the Conversions Controls 'add phrase' setting 
to the input value, wAddPhrase.  No checking is done for out of bounds values.


**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

wAddPhrase  -  the value to use for the Conversion Controls 'add phrase' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetAddPhrase(hCC, 0);  /* 0/1 - no phrase added or removed,
	     2   - add abbreviated DN,
	     3   - add alt name if it exists else DN,
	     4   - Remove all phrases and comments (default 0)  */

```
**See Also :**
[MMGetAddPhrase](/domino-c-api-docs/reference/Func/MMGetAddPhrase)
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
---
