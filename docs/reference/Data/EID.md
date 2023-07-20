##### Data Type : Extension Manager
##### EID - Extension manager function ID
---
```
#include <extmgr.h>
```

**Definition :**
```
typedef WORD EID
```

**Description :**

An EID number is used to identify a C API function in the Extension Manager facility.  This number is passed to EMRegister() to identify the function to be trapped, and also to the extension manager callback function to identify which function is being performed. See EM_xxx for acceptable values for EIDs.  Incorrect values will return an error from the function EMRegister().


**See Also :**
[EMHANDLER](/domino-c-api-docs/reference/Data/EMHANDLER)
[EMRECORD](/domino-c-api-docs/reference/Data/EMRECORD)
[EMRegister](/domino-c-api-docs/reference/Func/EMRegister)
---
