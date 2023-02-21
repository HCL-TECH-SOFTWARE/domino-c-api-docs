##### Function : MIME
##### MMGetInbLineLen - get Conversion Controls 'inbound line length' setting.
---
```
#include <mailmisc.h>
WORD LNPUBLIC MMGetInbLineLen(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetInbLineLen returns the Conversions Controls 'inbound line 
length' setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  if set, when converting MIME rich text parts to CD, justify using this right margin.  (text/plain parts are never justified) (default is 75)



**Sample Usage :**
```
WORD wInbLineLength;

wInbLineLength = MMGetInbLineLen(hCC);

```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMSetInbLineLen](/domino-c-api-docs/reference/Func/MMSetInbLineLen)
---
