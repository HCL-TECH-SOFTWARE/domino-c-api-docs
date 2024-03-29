##### Function : Domino Upgrade Services
##### DUSRetrieveFilters - Returns default filter strings.
---
```
#include <dus.h>
STATUS LNPUBLIC DUSRetrieveFilters(

	DHANDLE  hContext,
	DHANDLE *phDefaultFilters);
```
**Description :**

This function returns the default filter strings.

**Parameters :**
Input :
hContext  -   pointer to DUS specific context.  Allocated by the DUS in DUSStart and passed back to the DUS with every DUS function.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


phDefaultFilters  -  Allocated by the DUS, this is a list containing default filter strings that will be shown in the combobox.


**See Also :**
[DUSStart](/domino-c-api-docs/reference/Func/DUSStart)
[DUSStop](/domino-c-api-docs/reference/Func/DUSStop)
[DUSTerm](/domino-c-api-docs/reference/Func/DUSTerm)
---
