##### Data Type : Import/Export
##### EDITEXPORTDATA - Used in editor exports.
---
```
#include <ixedit.h>
```

**Definition :**

typedef struct
	{
	char InputFileName[OLDMAXPATH]; /* File to be read by export containing 
CD records */
	DHANDLE hCompBuffer;     /* Handle to composite buffer (V1 Exports) */
	DWORD CompLength;    /* Length of composite buffer (V1 Exports) */
	HEAD_DESC_BUFFER HeaderBuffer; 
	HEAD_DESC_BUFFER FooterBuffer;  
	PRINT_SETTINGS   PrintSettings;
	} EDITEXPORTDATA;


**Description :**

This structure is passed to all editor exports.


**See Also :**
[EDITIMPORTDATA](/domino-c-api-docs/reference/Data/EDITIMPORTDATA)
[EDITIXDATA](/domino-c-api-docs/reference/Data/EDITIXDATA)
---
