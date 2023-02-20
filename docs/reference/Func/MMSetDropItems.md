##### Function : MIME
##### MMSetDropItems - set Conversion Controls 'drop items setting' setting.
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetDropItems(

	CCHANDLE  hCC,
	char *pszDropItems);
```
**Description :**

The function  MMSetDropItems sets the Conversions Controls 'drop items setting' 
setting to the input value, pszDropItems.  The pszDropItems string is a comma 
delimited list of items to drop during export.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

pszDropItems  -  the value to use for the Conversion Controls 'drop items setting' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
char *pszDropItems = "$MIMETrack, $Mailer";

MMSetDropItems(hCC, pszDropItems); /* Comma delimited list of item names to 
remove from msgs as they are exported (default is NULL) */

```
**See Also :**
[MMGetDropItems](/reference/Func/MMGetDropItems)
[CCHANDLE](/reference/Data/CCHANDLE)
---
