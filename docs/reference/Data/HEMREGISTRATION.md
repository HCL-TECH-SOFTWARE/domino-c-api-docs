##### Data Type : Extension Manager
##### HEMREGISTRATION - Extension Manager context handle

---
```
#include <extmgr.h>
```

**Definition :**

typedef DWORD HEMREGISTRATION;

**Description :**

When an extension is successfully registered to the Extension Manager, a handle to that registration context is returned from EMRegister().  This handle must be used when calling EMDeregister() to remove the extension.


**See Also :**
[EMDeregister](/domino-c-api-docs/reference/Func/EMDeregister)
[EMRegister](/domino-c-api-docs/reference/Func/EMRegister)
---
