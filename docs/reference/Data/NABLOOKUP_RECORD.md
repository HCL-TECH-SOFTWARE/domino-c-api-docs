##### Data Type : Name & Address Book
##### NABLOOKUP_RECORD - NAB lookup record structure. 
---
```
#include <nlookup.h>
```

**Definition :**

typedef struct {
	char  *pUserName;
	char  *pAltUserName;
	char  *pAltUserNameLang;
	char  *pOldWebName;
	char  *pInternetAddress;
	char  *pSSOTokenUserName;
	void  *pReserved;
} NABLOOKUP_RECORD;


**Description :**

NAB lookup record structure. 


**See Also :**
---
