##### Data Type : Recovery
##### RECOVERY_INFO - Recovery info structure.
---
```
#include <kfm.h>
```

**Definition :**

typedef	struct {
	WORD Quorum;
	WORD NumberOfRAs;
	WORD RALength[8];
	char	RAs[8][MAXUSERNAME+1];
	WORD RecoveryPasswordLength;
	char	MailAddress[MAXPATH+1];
	char	CustomMsg[MAX_IDRecovery_CustomMessage];
} RECOVERY_INFO;

**Description :**

Recovery info structure.


**See Also :**
---
