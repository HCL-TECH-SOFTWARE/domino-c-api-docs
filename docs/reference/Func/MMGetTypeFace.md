##### Function : MIME
##### MMGetTypeFace - get Conversion Controls 'typeface' setting
---
```
#include <mailmisc.h>
WORD LNPUBLIC MMGetTypeFace(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetTypeFace returns the Conversions Controls 'typeface' 
setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  0 - Times Roman
              1 - Helvetica
              2 - Courier (default)



**Sample Usage :**
```
WORD wTypeFace;

wTypeFace = MMGetTypeFace(hCC);


```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMSetTypeFace](/domino-c-api-docs/reference/Func/MMSetTypeFace)
---
