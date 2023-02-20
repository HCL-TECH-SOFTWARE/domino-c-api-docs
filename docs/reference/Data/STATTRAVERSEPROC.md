##### Data Type : Statistics Reporting
##### STATTRAVERSEPROC - Action routine for each statistic found by StatTraverse().
---
```
#include <stats.h>
```
**Description :**

This typedef defines the interface to the routine called by StatTraverse().  
Under Windows, the routine must be exported in the application's .DEF file.

The address of a routine with this interface is passed as a parameter to 
StatTraverse().  The routine will be called once for each statistic found.  The 
first parameter is supplied in the call to StatTraverse() and is used in the 
case where the caller of StatTraverse() needs to pass data to this routine.  If 
this routine returns an error, the traversal will halt and return that error.

**See Also :**
[StatTraverse](/reference/Func/StatTraverse)
---
