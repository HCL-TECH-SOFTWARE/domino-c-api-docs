##### Symbolic Value : iCalendar
##### CAL_NOTEOPEN_xxx - Flags that control behavior of the calendar APIs - Used when opening a note handle for calendar data.
---
```
#include <calapi.h>
```

**Symbolic Values :**

	CAL_NOTEOPEN_HANDLE_NOSPLIT	  -  Used when getting a handle via CalOpenNoteHandle (Handy for read-only cases).When a specific instance of a recurring entry is requested, the underlying note may represent multiple instances. Default behavior makes appropriate modifications so that the returned handle represents a single instance (but this might cause notes to be created or modified as a side effect). Using CAL_NOTEOPEN_HANDLE_NOSPLIT will bypass any note creations or modifications and return a note handle that may represent more than a single instance on the calendar.


**Description :**




**See Also :**
---
