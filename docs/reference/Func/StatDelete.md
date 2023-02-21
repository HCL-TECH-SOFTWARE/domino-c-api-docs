##### Function : Statistics Reporting
##### StatDelete - Deletes all occurrences of a statistic.
---
```
#include <stats.h>
void LNPUBLIC StatDelete(

	const char far *Facility,
	const char far *StatName);
```
**Description :**

This function deletes all occurrences of a statistic.

**Parameters :**
Input :
Facility  -  Name of facility.  See Symbolic Value, STATPKG_xxx for a list of existing Domino facilities.

StatName  -  Name of statistic.

Output :
(routine)  -  None



**See Also :**
[STATPKG_xxx](/domino-c-api-docs/reference/Symb/STATPKG_xxx)
---
