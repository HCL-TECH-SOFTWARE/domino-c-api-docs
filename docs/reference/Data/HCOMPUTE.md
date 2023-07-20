##### Data Type : Handles
##### HCOMPUTE - A handle to a compiled formula.
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef void far * HCOMPUTE;
```

**Description :**

An HCOMPUTE is a handle to a compiled formula.   The handle is assigned by calling NSFComputeStart.  The function NSFComputeEvaluate takes an HCOMPUTE as input to uniquely identify the formula to be evaluated.  The HCOMPUTE is freed by calling NSFComputeStop.


**See Also :**
[NSFComputeEvaluate](/domino-c-api-docs/reference/Func/NSFComputeEvaluate)
[NSFComputeStart](/domino-c-api-docs/reference/Func/NSFComputeStart)
[NSFComputeStop](/domino-c-api-docs/reference/Func/NSFComputeStop)
---
