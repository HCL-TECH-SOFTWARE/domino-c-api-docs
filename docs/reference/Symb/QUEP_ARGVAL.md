##### Symbolic Value : 
##### QUEP_ARGVAL - Query Argument Value
---
```
#include <dbmiscods.h>
```

**Symbolic Values :**



**Description :**




**Sample Usage :**
```
	typedef struct { 
	 WORD type; /* Standard NSF types: TYPE_TEXT, TYPE_NUMBER, TYPE_TIME. 
*/ 
	 DWORD length; /* For all textual values. */ 
	 DWORD ordinal; /* The nth argument in the query (so, the list needn't 
be in order). */ 
	 BOOL bBinaryForm; /* Whether NUMBER and DATETIME values have been 
created in the Value area. */ 
	 /* Argument names can only be 16 bytes long. */ 
	 char ArgName[16]; 
	 char Value[256]; /* The stringized value. */ 
	} QUEP_ARGVAL
```

**See Also :**
---
