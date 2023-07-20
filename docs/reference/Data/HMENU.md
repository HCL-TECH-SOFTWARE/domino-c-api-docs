##### Data Type : Menu Add-In
##### HMENU - *OBSOLETE* Type definition for hmenu member of  NAM_INITMENU_INFO for OS/2 and UNIX platforms.
---
```
#include <addinmen.h>
```

**Definition :**
```
#ifdef UNIX
#define HMENU        HWND
#endif
#ifdef OS2
#define HMENU        HWND
#endif
```

**Description :**

<b>	</b>***OBSOLETE ***<br>
<br>
Type definition for hmenu member of  NAM_INITMENU_INFO for OS/2 and UNIX platforms.


**See Also :**
[NAM_INITMENU_INFO](/domino-c-api-docs/reference/Data/NAM_INITMENU_INFO)
---
