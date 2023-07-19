##### Data Type : nao
##### NAO_ENTRY_RESOURCE - Entry resource structure.
---
```
#include <addinout.h>
```

**Definition :**

typedef union
{
	char    szFormula[NAO_LENGTH_FORMULA];  /* Formula */
	char    szURL[NAO_LENGTH_URL];   /* URL */
	DBHANDLE   hDb;     /* Database */
	NOTEHANDLE   hNote;     /* Note */
	NOTELINK   nlNoteLink;    /* Link */
} NAO_ENTRY_RESOURCE;

**Description :**

Entry resource structure.


**See Also :**
---
