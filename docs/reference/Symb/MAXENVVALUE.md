##### Symbolic Value : Limits
##### MAXENVVALUE - Maximum environment variable string size.
---
```
#include <osenv.h>
```
**Description :**

MAXENVVALUE is used to declare storage for OS environment variable strings.  By 
declaring a string array of this length,  a caller of OSGetEnvironmentString is 
assured that the array will be large enough to hold the worst-case (largest) 
environment variable string.  This size includes the terminating null.

**See Also :**
[OSGetEnvironmentString](/reference/Func/OSGetEnvironmentString)
---
