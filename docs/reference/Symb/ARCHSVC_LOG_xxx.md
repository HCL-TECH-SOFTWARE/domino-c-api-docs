##### Symbolic Value : archiving service
##### ARCHSVC_LOG_xxx - Controls tracing/debug output These should be "FLAGS" so that we can get "just enough" output.
---
```
#include <archsvc.h>
```

**Symbolic Values :**

	ARCHSVC_LOG_ERROR	  -  Enables tracing on all error returns so that callers can see the origin of a low level API error.

	ARCHSVC_LOG_DEBUG	  -  Enables the debug dump of key data structures during the export/import process.

	ARCHSVC_LOG_ENTRYEXIT	  -  Logs the entry/exit of all archiving service functions along with argument and return values. This will help support pinpoint the cause of any errors that may occur.


**Description :**

The archiving functions have the ability to output trace information to the file specified in the DEBUG_OUTFILE notes ini setting. Tracing is enabled via the LOG_ARCHSVC notes ini variable.


**See Also :**
---
