##### Data Type : nao
##### NAO_DRAGDROP_DOC - Drag/drop doc structure
---
```
#include <addinout.h>
```

**Definition :**

typedef struct
{
	DWORD    dwSize;     /* Size of this structure */
	BOOL    bMove;     /* TRUE if MOVE, FALSE if COPY */
	DWORD    dwCount;    /* Number of documents being dropped */
	DBHANDLE   hSourceDb;    /* Source database handle for these notes */
	HANDLE    hIDTable;    /* ID table of documents to drop into folder */
	DBHANDLE   hDestDb;    /* Destination database handle for these notes */
	NAO_SELECT_INFO   DestFolderInfo;    /* NAO_SELECT_INFO of destination 
folder */
	BOOL    bNamedFolder;    /* TRUE if destination folder has a named 
folder element */
	BOOL    bActionEntry;    /* TRUE if destination folder has a action 
element */
	DWORD    dwReserved1;    /* Reserved */
	DWORD    dwReserved2;    /* Reserved */
} NAO_DRAGDROP_DOC;

**Description :**

Drag/drop doc structure.


**See Also :**
---
