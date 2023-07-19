##### Data Type : Views
##### VIEW_COLUMN_FORMAT5 - Extended View column format descriptor.
---
```
#include <viewfmt.h>
```

**Definition :**

typedef struct
	{
	WORD Signature;   /* VIEW_COLUMN_FORMAT_SIGNATURE5 */
	WORD dwLength;   /* sizeof this structure + any extra data. */
	/* Names style formatting data. */
	DWORD dwFlags;  
	WORD wDistNameColLen;  /* Length of programatic name of column that 
contains distiguished name. */
	WORD wSharedColumnAliasLen; /* If shared column, length of the alias of 
the shared column */
	DWORD dwReserved[4];  /* Reserved for future use. */
	} VIEW_COLUMN_FORMAT5;

**Description :**




**See Also :**
[VCF5_xxx](/domino-c-api-docs/reference/Symb/VCF5_xxx)
[VIEW_COLUMN_FORMAT](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT)
[VIEW_COLUMN_FORMAT_SIGNATURE5](/domino-c-api-docs/reference/Symb/VIEW_COLUMN_FORMAT_SIGNATURE5)
[VIEW_TABLE_FORMAT](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT)
[VIEW_TABLE_FORMAT2](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT2)
---
