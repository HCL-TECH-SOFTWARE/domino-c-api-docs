##### Function : Statistics Reporting
##### StatQueryTime - Returns the specified statistic in a formatted statistics buffer.
---
```
#include <stats.h>
STATUS LNPUBLIC StatQueryTime(

	char far *Facility,
	char far *StatName,
	char far *HeaderString,
	char far *NamePrefix,
	char far *ValuePrefix,
	char far *LineSuffix,
	DHANDLE far *rethStats,
	DWORD far *retStatsLength);
```
**Description :**

This function traverses the specified statistic or can traverse all statistics 
and returns the statistics information in a formatted statistics buffer.  The 
information includes the time each statistic was last updated.  This function 
is similar to StatQuery.  StatQuery traverses all statistics (you cannot 
specify a specific statistic) and does not include the time each statistic was 
last updated.

**Parameters :**
Input :
Facility  -  Optional.  Name of facility.  Usee NULL for all facilities.  See Symbolic Value, STATPKG_xxx for a list of facilities monitored by Domino.

StatName  -  Optional.  Name of statistic.  Use NULL for all statistics.

HeaderString  -  Optional.  Pointer to a NULL terminated string to be inserted at the start of the returned buffer.  Use NULL if no string is desired.

NamePrefix  -  Pointer to a NULL terminated string of characters to precede the statistic name.

ValuePrefix  -  Pointer to a NULL terminated string of characters to precede the statistics value. 

LineSuffix  -  Pointer to a NULL terminated string of characters that will terminate the statistics value (ie:  "\n").

Output :
(routine)  -  Return status from this call -- indicates either success (NOERROR) or what the error is.  An error will stop the traversal.


rethStats  -  Handle to the returned formatted statistics buffer.  Use OSLock to obtain a pointer to this buffer and OSMemFree to release the storage.  The buffer will be NULL terminated.

retStatsLength  -  Length of data in the returned formatted statistics buffer.


**See Also :**
[StatQuery](/reference/Func/StatQuery)
[StatTraverse](/reference/Func/StatTraverse)
---
