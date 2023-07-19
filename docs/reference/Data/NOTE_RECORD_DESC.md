##### Data Type : Note
##### NOTE_RECORD_DESC - Note record descriptor
---
```
#include <addinout.h>
```

**Definition :**

typedef struct {
	DWORD dwRecordType;   /* ODS type of extension record              */
	DWORD dwRecordUsage;   /* Unique ID to identify purpose of record   */
	DWORD dwTotalExtenSize;   /* Size of extension record + variable data  
*/
	DWORD dwFlags;    /* Flags, undefined bits MBZ. Defined below. */
} NOTE_RECORD_DESC;

**Description :**

Note record descriptor: Used to describe another record, called the target record.  This record can be used to make ODS data extensible. The initial use is to allow for current and future extensions to the NOTE_SEAL2_HDR and NOTE_SEAL2 records. 


**See Also :**
---
