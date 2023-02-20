##### Function : MIME
##### MMGetOutbLineLen - get Conversion Controls 'outbound line length' setting.
---
```
#include <mailmisc.h>
WORD LNPUBLIC MMGetOutbLineLen(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetOutbLineLen returns the Conversions Controls 'outbound line 
length' setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  if set, when convert CD to MIME, justify using this right margin(default is 75)



**Sample Usage :**
```
WORD wOutbLineLength;

wOutbLineLength = MMGetOutbLineLen(hCC);

```
**See Also :**
[CCHANDLE](/reference/Data/CCHANDLE)
[MMSetOutbLineLen](/reference/Func/MMSetOutbLineLen)
---
