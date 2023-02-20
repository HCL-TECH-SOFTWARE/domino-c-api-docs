##### Function : HTML
##### HTMLDestroyConverter - Destroy the converter.
---
```
#include <htmlapi.h>
STATUS LNPUBLIC HTMLDestroyConverter(

	HTMLHANDLE  hHTML);
```
**Description :**

Destroy the converter.

**Parameters :**
Input :
hHTML  -  handle of the converter to destroy.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



**See Also :**
[HTMLCreateConverter](/reference/Func/HTMLCreateConverter)
[HTMLHANDLE](/reference/Data/HTMLHANDLE)
---
