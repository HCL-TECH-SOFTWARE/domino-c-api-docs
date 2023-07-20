##### Data Type : nao
##### NAO_SELECT_INFO - Select infomation structure
---
```
#include <addinout.h>
```

**Definition :**
```
typedef struct
{
	DWORD    dwSize;      /* Size of this structure */
	NAO_ENTRY_DATA   EntryData;     /* NAO_ENTRY_DATA */
	WORD    wLevel;      /* Outline level, root = 0 */
	BOOL    bNeedsRefresh;     /* Indicates outline refresh is needed */
	DWORD    dwReserved1;     /* Reserved */
	DWORD    dwReserved2;     /* Reserved */
} NAO_SELECT_INFO;
```

**Description :**

Select infomation structure.


**See Also :**
---
