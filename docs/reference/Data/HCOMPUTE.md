##### Data Type : Handles
##### HCOMPUTE - A handle to a compiled formula.
---
```
#include <nsfdata.h>
```
**Description :**

An HCOMPUTE is a handle to a compiled formula.   The handle is assigned by 
calling NSFComputeStart.  The function NSFComputeEvaluate takes an HCOMPUTE as 
input to uniquely identify the formula to be evaluated.  The HCOMPUTE is freed 
by calling NSFComputeStop.

**See Also :**
[NSFComputeEvaluate](/reference/Func/NSFComputeEvaluate)
[NSFComputeStart](/reference/Func/NSFComputeStart)
[NSFComputeStop](/reference/Func/NSFComputeStop)
---
