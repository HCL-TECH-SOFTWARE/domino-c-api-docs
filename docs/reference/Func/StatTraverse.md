##### Function : Statistics Reporting
##### StatTraverse - Traverse the statistic(s) for one or more facilities.
---
```
#include <stats.h>
void LNPUBLIC StatTraverse(

	char far *Facility,
	char far *StatName,
	STATTRAVERSEPROC  Routine,
	void far *Context);
```
**Description :**

This function traverses one or more statistics for one or more facilities.  It 
calls a user defined routine, called a traversal routine, for each statistic 
found.

**Parameters :**
Input :
Facility  -  Name of facility (NULL for all facilities).  See Symbolic Value, STATPKG_xxx for a list of facilities monitored by Domino.

StatName  -  Name of statistic (NULL for all statistics).

Routine  -  Pointer to the user defined traversal routine.  This routine is called once for each statistic found.

The definition of STATTRAVERSEPROC is:

STATUS (LNCALLBACKPTR Routine)
                    (void far *Context,         /* Pointer to data passed to
                                                                  StatTraverse to be given to this routine */
                      char far *Facility,         /* Facility name */
                      char far *StatName,    /* Name of statistic */
                      WORD ValueType,     /* Value type of the statistic:
                                                                     VT_LONG, VT_TEXT,
                                                                     VT_TIMEDATE, VT_NUMBER */
                      void far *Value);          /* Value of the statistic */

If the traversal routine returns an error, the traversal stops.

Context  -  The traversal routine context block - a pointer to data to be sent to the user defined traversal routine.

Output :
(routine)  -  None



**Sample Usage :**
```

StatTraverse(FacilTable[i],        /* name of facility */
             NULL,                 /* traverse all stats */
             DisplayTrav,          /* callback function */
             (void *)&hCompound);  /* param passed to callback
                                      function */

```
**See Also :**
[STATPKG_xxx](/reference/Symb/STATPKG_xxx)
[StatQuery](/reference/Func/StatQuery)
[StatToText](/reference/Func/StatToText)
---
