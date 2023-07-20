##### Data Type : Database
##### DBACTIVITY_ENTRY_EXTENDED - Database user session activity extended structure.
---
```
#include <nsfdb.h>
```

**Definition :**
```
typedef struct {
	TIMEDATE Time;    /* Time of record */
	ACTIVITY_ENTRY_DETAILS_DUP AEDetails;
	DWORD UserNameOffset;         /* Offset of the user name from the 
beginning of this memory block */
	      /* User names follow -- '\0' terminated */ 
} DBACTIVITY_ENTRY_EXTENDED;

```

**Description :**

Database user session activity extended structure.


**See Also :**
---
