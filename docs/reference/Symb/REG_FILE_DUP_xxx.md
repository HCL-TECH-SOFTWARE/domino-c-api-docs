##### Symbolic Value : User Registration
##### REG_FILE_DUP_xxx - Determine the action When the registration API finds a duplicate Mail File or Roaming folder. 
---
```
#include <reg.h>
```

**Symbolic Values :**

	EG_FILE_DUP_STOP	  -  When a duplicate is found, registration should stop.

	REG_FILE_DUP	  -  When a duplicate is found, registration should generate a unique name and continue

	REG_FILE_DUP	  -  When a duplicate is found, registration should continue by using the name (possibly overwriting the file)


**Description :**

These symobls are used to determine the action that the registration API should take when finding a duplicate Mail File or Roaming folder.<font color="#0000FF"> </font>


**See Also :**
[REG_MAIL_INFO_EXT](/domino-c-api-docs/reference/Data/REG_MAIL_INFO_EXT)
[REG_ROAMING_INFO](/domino-c-api-docs/reference/Data/REG_ROAMING_INFO)
---
