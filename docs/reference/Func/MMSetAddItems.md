##### Function : Mail
##### MMSetAddItems - set Conversion Controls 'add items setting' setting.
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetAddItems(

	CCHANDLE  hCC,
	char *pszAddItems);
```
**Description :**

The function  MMSetAddItems sets the Conversions Controls 'add items setting' 
setting to the input value, pszAddItems.  The pszAddItems string is a comma 
delimited list of items to add (i.e., preserve) during export.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

pszAddItems  -  the value to use for the Conversion Controls 'add items setting' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
char *pszAddItems = "$Setting1, $Setting2";

MMSetAddItems(hCC, pszAddItems); /* Comma delimited list of item names to 
preserve in msgs as they are exported (default is "") */

```
**See Also :**
[MMGetAddItems](/domino-c-api-docs/reference/Func/MMGetAddItems)
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
---
