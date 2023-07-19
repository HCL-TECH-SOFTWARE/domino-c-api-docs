##### Symbolic Value : archiving service
##### ARCHIVE_ATTACH_xxx - Indicates the type of attachment.
---
```
#include <archsvc.h>
 ARCHIVE_ATTACH_xxx(

	  ARCHIVE_ATTACH_ENCRYPTED,
	  ARCHIVE_ATTACH_MACBIN_RAW,
	  ARCHIVE_ATTACH_RAW);
```

**Symbolic Values :**

	ARCHIVE_ATTACH_ENCRYPTED	  -  Indicates attachment is being passed encrypted.

	ARCHIVE_ATTACH_MACBIN_RAW	  -  Indicates attachment data is mac binary data as stored in NSF (compressed data and resource fork only).

	ARCHIVE_ATTACH_RAW	  -  Indicates that this is not a file attachment but object data known only to notes.


**Description :**




**Parameters :**




**See Also :**
[ARCHIVEATTACHINIT](/domino-c-api-docs/reference/Data/ARCHIVEATTACHINIT)
---
