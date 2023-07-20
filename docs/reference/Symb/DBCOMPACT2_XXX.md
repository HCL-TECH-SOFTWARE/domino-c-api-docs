##### Symbolic Value : Database
##### DBCOMPACT2_XXX - This value reflects allow customers to turn on/off design compression, data compression and DAOS for a given database
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DBCOMPACT2_COMPRESS_DESIGN_NS	  -  TRUE if design note non-summary should be compressed

	DBCOMPACT2_UNCOMPRESS_DESIGN_NS	  -  TRUE if design note non-summary should be uncompressed

	DBCOMPACT2_COMPRESS_DATA_DOCS	  -  TRUE if all data note non-summary should be compressed

	DBCOMPACT2_UNCOMPRESS_DATA_DOCS	  -  TRUE if all data note non-summary should be uncompressed

	DBCOMPACT2_FORCE_DAOS_ON	  -  Enable compact TO DAOS

	DBCOMPACT2_FORCE_DAOS_OFF	  -  Enable compact FROM DAOS

	DBCOMPACT2_FORCE_PIRC_ON	  -  Enable compact WITH PIRC

	DBCOMPACT2_FORCE_PIRC_OFF	  -  Enable compact WITHOUT PIRC


**Description :**

This value reflects allow customers to turn on/off design compression, data compression and DAOS for a given database


**See Also :**
---
