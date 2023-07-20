##### Symbolic Value : Database
##### INFOPARSE_xxx - Specifies which piece of information to access from the database information buffer.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	INFOPARSE_TITLE	  -  database title.

	INFOPARSE_CATEGORIES	  -  database categories.

	INFOPARSE_CLASS	  -  template name (for a design template database).

	INFOPARSE_DESIGN_CLASS	  -  inherited template name (for a database that inherited its design from a design template).


**Description :**

These values specify which piece of information to access out of the four pieces of information contained in the database information buffer.


**See Also :**
[NSFDbInfoModify](/domino-c-api-docs/reference/Func/NSFDbInfoModify)
[NSFDbInfoParse](/domino-c-api-docs/reference/Func/NSFDbInfoParse)
---
