##### Data Type : Views
##### NIFFINDBYKEYCTX - Structure of context for NIFFindbyKeyExtended4
---
```
#include <nif.h>
```

**Definition :**
```
typedef struct NIFFindByKeyContext {
	WORD	EntriesThisChunk;
	WORD	wSizeOfChunk;
	void	*SummaryBuffer;
	MEMHANDLE hUserData;
	DWORD	UserDataLen;
	DWORD	TotalDataInBuffer;
} NIFFINDBYKEYCTX;
```

**Description :**

NIFFindByKeyExtended4 features a callback per chunk of summary, so the whole summary can
	be returned while the Collection remains locked r/w


**See Also :**
[NIFFindByKeyExtended4](/domino-c-api-docs/reference/Func/NIFFindByKeyExtended4)
---
