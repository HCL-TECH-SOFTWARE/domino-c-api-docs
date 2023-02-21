##### Function : MIME
##### MMGetPointSize - get Conversion Controls 'point size' setting.
---
```
#include <mailmisc.h>
WORD LNPUBLIC MMGetPointSize(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetPointSize returns the Conversions Controls 'point size' 
setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  one of: 6, 8, 9, 10 (default), 12, 14, 18, 24



**Sample Usage :**
```
WORD wPointSize;

wPointSize = MMGetPointSize(hCC);

```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMSetPointSize](/domino-c-api-docs/reference/Func/MMSetPointSize)
---
