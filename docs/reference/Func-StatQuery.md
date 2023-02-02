##### Function : Statistics Reporting
##### StatQuery - Returns all statistics in a formatted statistics buffer.
---
##### #include <stats.h>
STATUS LNPUBLIC **StatQuery(**

	char far *HeaderString,
	char far *NamePrefix,
	char far *ValuePrefix,
	char far *LineSuffix,
	DHANDLE far *rethStats,
	DWORD far *retStatsLength);
**Description :**
This function traverses all statistics and returns all statistics in a 
formatted statistics buffer.  
**Parameters :**
Input :
HeaderString  -  Optional.  Pointer to a NULL terminated string to be inserted at the start of the returned buffer.  Use NULL if no string is desired.

NamePrefix  -  Pointer to a NULL terminated string of characters to precede the statistic name.

ValuePrefix  -  Pointer to a NULL terminated string of characters to precede the statistics value. 

LineSuffix  -  Pointer to a NULL terminated string of characters that will terminate the statistics value (ie:  "\n").

Output :
(routine)  -  Return status from this call -- indicates either success (NOERROR) or what the error is.  An error will stop the traversal.


rethStats  -  Handle to the returned formatted statistics buffer.  Use OSLock to obtain a pointer to this buffer and OSMemFree to release the storage.  The buffer will be NULL terminated.

retStatsLength  -  Length of data in the returned formatted statistics buffer.

**See Also :**
[StatQueryTime](D:/md_files/StatQueryTime.md)
[StatTraverse](D:/md_files/StatTraverse.md)
---
