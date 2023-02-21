##### Function : MIME
##### MMGetCharSetDetect - get Conversion Controls 'character set detection' setting
---
```
#include <mailmisc.h>
BOOL LNPUBLIC MMGetCharSetDetect(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetCharSetDetect returns the Conversions Controls 'character 
set detection' setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  if TRUE auto-detect if necessary when converting MIME to CD (default is FALSE).



**Sample Usage :**
```
BOOL bCharSetDetect;

bCharSetDetect = MMGetCharSetDetect(hCC);

```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMSetCharSetDetect](/domino-c-api-docs/reference/Func/MMSetCharSetDetect)
---
