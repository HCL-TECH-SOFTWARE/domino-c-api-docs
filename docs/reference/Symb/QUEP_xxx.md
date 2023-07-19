##### Symbolic Value : 
##### QUEP_xxx - Some of the query setting flags.
---
```
#include <dbmisc.h>
```

**Symbolic Values :**

	QUEP_NO_EXEC	  -  Explain only mode, only plan and return the explain output.

	QUEP_DEBUG	  -  Produce debugging output (notes.ini setting is independent of this).

	QUEP_VIEWREFRESH	  -  Refresh all views when they are opened(default is NO_UPDATE).

	QUEP_PARSEONLY	  -  To check for syntax only - stops short of planning.

	QUEP_EXPLAIN	  -  Governs producing Explain output.

	QUEP_DSGNCATREFRESH	  -  Before running the query, build/refresh the design catalog, will have no effect if you have less than Designer privileges on the database.

	QUEP_DSGNCATREBUILD	  -  Before running the query, rebuild the design catalog, will have no effect if you have less than Designer privileges on the database.


**Description :**




**See Also :**
---
