##### Data Type : Statistics Reporting
##### STATTRAVERSEPROC - Action routine for each statistic found by StatTraverse().
---
```
#include <stats.h>
```

**Definition :**
```
typedef STATUS (LNPCALLBACKPTR STATTRAVERSEPROC)(
   void far *, /* Context   - ptr to data passed to StatTraverse to
                              be given to this routine */
   char far *, /* Facility  - facility name */
   char far *, /* StatName  - name of statistic */
   WORD,       /* ValueType - see VT_xxx */
   void far *  /* Value     - value of the statistic */
);
```

**Description :**

This typedef defines the interface to the routine called by StatTraverse().  Under Windows, the routine must be exported in the application's .DEF file.<br>
<br>
The address of a routine with this interface is passed as a parameter to StatTraverse().  The routine will be called once for each statistic found.  The first parameter is supplied in the call to StatTraverse() and is used in the case where the caller of StatTraverse() needs to pass data to this routine.  If this routine returns an error, the traversal will halt and return that error.


**See Also :**
[StatTraverse](/domino-c-api-docs/reference/Func/StatTraverse)
---
