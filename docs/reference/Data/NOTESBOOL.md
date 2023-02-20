##### Data Type : Mixed 32/16-bit Model
##### NOTESBOOL - * OBSOLETE * Mixed 32/16-bit Boolean parameter
---
```
#include <global.h>
```
**Description :**

***OBSOLETE - Included for backward compatibility only***

The "value" of a logical expression in the C language is defined to be an 
integer value where 0 indicates false and a non-zero value indicates true.  The 
size of an integer varies between platforms, which implies that the size of a 
Boolean argument to a function will also vary.  To ensure that the size of 
Boolean arguments passed to Notes API functions are the correct size, the 
parameters are declared in the API header files with the type "NOTESBOOL".  In 
the mixed 32/16-bit model, this type is defined to be an "unsigned short" value 
(16 bits long).  On all other platforms, this type is defined to be an 
"unsigned int" (16 or 32 bits, depending on the target platform).

**See Also :**
---
