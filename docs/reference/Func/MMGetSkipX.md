##### Function : MIME
##### MMGetSkipX - get Conversion Controls 'skip X-Notes-Item headers' setting.
---
```
#include <mailmisc.h>
BOOL LNPUBLIC MMGetSkipX(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetSkipX returns the Conversions Controls 'skip X-Notes-Item 
headers' setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  if TRUE, don't export any headers named x-notes-item (default FALSE)



**Sample Usage :**
```
BOOL bSkipX;

bSkipX = MMGetSkipX(hCC);

```
**See Also :**
[CCHANDLE](/reference/Data/CCHANDLE)
[MMSetSkipX](/reference/Func/MMSetSkipX)
---
