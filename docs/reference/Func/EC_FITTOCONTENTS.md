##### Function : Rich Text
##### EC_FITTOCONTENTS - Evaluates the Flags member of CDEMBEDDEDCTL against EC_FLAG_UNITS
---
```
#include <editods.h>
BOOL EC_FITTOCONTENTS(

	WORD  flags);
```
**Description :**

Implemented as a macro:

#define EC_FITTOCONTENTS(flags) ((flags & EC_FLAG_UNITS) == 
EC_FLAG_FITTOCONTENTS)

**Parameters :**
Input :
flags  -  EC_FLAG_xxx

Output :
(routine)  -  Returns TRUE if width/height of specified flag are in dialog units, not twips, FALSE otherwise.  



**See Also :**
[EC_FLAG_xxx](/domino-c-api-docs/reference/Symb/EC_FLAG_xxx)
[CDEMBEDDEDCTL](/domino-c-api-docs/reference/Data/CDEMBEDDEDCTL)
---
