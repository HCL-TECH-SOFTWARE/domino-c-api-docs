##### Symbolic Value : iCalendar
##### READ_RANGE_MSAK2_xxx - Bits that control what properties about the calendar entries will be returned in addition to those defined in dwReturnMask.
---
```
#include <calapi.h>
```

**Symbolic Values :**

	READ_RANGE_MASK2_HASATTACH	  -  X-LOTUS-HASATTACH is set to 1 if there are any file attachments for this entry.

	READ_RANGE_MASK2_UNID	  -  X-LOTUS-UNID will always be set for notices (as it is used as the identifier for a notice), but setting this flag will also set X-LOTUS-UNID for calendar entries, where this will be set with the UNID of the note that currently contains this instance (can be used to construct a URL to open the instance in Notes, for instance).


**Description :**




**See Also :**
---
