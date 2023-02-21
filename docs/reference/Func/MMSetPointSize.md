##### Function : MIME
##### MMSetPointSize - set Conversion Controls 'point size' setting
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetPointSize(

	CCHANDLE  hCC,
	WORD  wPointSize);
```
**Description :**

The function  MMSetPointSize sets the Conversions Controls 'point size' setting 
to the input value, wPointSize.  No checking is done for out of bounds values.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

wPointSize  -  the value to use for the Conversion Controls 'point size' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetPointSize(hCC, 10); /* one of: 6, 8, 9, 10 (default), 12, 14, 18, 24 */
```
**See Also :**
[MMGetPointSize](/domino-c-api-docs/reference/Func/MMGetPointSize)
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
---
