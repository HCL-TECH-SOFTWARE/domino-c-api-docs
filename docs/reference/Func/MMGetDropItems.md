##### Function : MIME
##### MMGetDropItems - get Conversion Controls 'drop items' setting
---
```
#include <mailmisc.h>
char * LNPUBLIC MMGetDropItems(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetDropItems returns the Conversions Controls 'drop items' 
setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  Comma delimited list of item names to remove from msgs as they are exported (default is NULL)



**Sample Usage :**
```
char * pszDropItems;

pszDropItems = MMGetDropItems(hCC);

```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMSetDropItems](/domino-c-api-docs/reference/Func/MMSetDropItems)
---
