##### Function : MIME
##### MMGetStripGroups - get Conversion Controls 'strip groups from addresses' setting
---
```
#include <mailmisc.h>
BOOL LNPUBLIC MMGetStripGroups(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetStripGroups returns the Conversions Controls 'strip groups 
from addresses' setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  if TRUE strip groups from all addresses when importing (default is FALSE)



**Sample Usage :**
```
BOOL bStripGroups;

bStripGroups = MMGetStripGroups(hCC);

```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMSetStripGroups](/domino-c-api-docs/reference/Func/MMSetStripGroups)
---
