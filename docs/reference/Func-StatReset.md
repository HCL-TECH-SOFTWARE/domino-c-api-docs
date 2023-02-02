##### Function : Statistics Reporting
##### StatReset - Set a numeric-additive statistic to 0.
---
##### #include <stats.h>
STATUS LNPUBLIC **StatReset(**

	const char *Facility,
	const char *StatName);
**Description :**
This function will set the value of a numeric-additive statistic (a statistic 
of type VT_LONG or VT_NUMBER and is additive) to 0.  This function performs the 
same operation as the Set Stat Domino Server console command.  For more 
information on this operation, refer to the Administering the Domino System 
documentation..
**Parameters :**
Input :
Facility  -  Null-terminated string containing the name of the facility.

StatName  -  Null-terminated string containing the name of the statistic.

Output :
(routine)  -  Return status from this call:

NOERROR - Success

ERR_STAT_NOT_SET - Unable to set the specified statistic to 0.

ERR_STAT_NOT_FOUND - Statistic is not in the Lotus Domino Server's statistic table.

ERR_xxx - Errors returned by lower level Notes functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


**See Also :**
[STATPKG_xxx](D:/md_files/STATPKG_xxx.md)
[StatTraverse](D:/md_files/StatTraverse.md)
[StatUpdate](D:/md_files/StatUpdate.md)
---
