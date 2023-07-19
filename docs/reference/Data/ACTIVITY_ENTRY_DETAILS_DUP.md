##### Data Type : Database
##### ACTIVITY_ENTRY_DETAILS_DUP - Database Activity Structure.
---
```
#include <nsfdb.h>
```

**Definition :**

typedef struct {
	WORD DataReads;   /* # of data notes read */
  WORD DataAdds;   /* # of data notes added */
	WORD DataUpdates;   /* # of data notes updated */
	WORD DataDeletes;   /* # of data notes deleted */
	WORD NonDataReads;   /* # of nondata notes read */
  WORD NonDataAdds;   /* # of nondata notes added */
	WORD NonDataUpdates;    /* # of nondata notes updated */
	WORD NonDataDeletes;    /* # of nondata notes deleted */
} ACTIVITY_ENTRY_DETAILS_DUP;


**Description :**

Database Activity Structure.


**See Also :**
---
