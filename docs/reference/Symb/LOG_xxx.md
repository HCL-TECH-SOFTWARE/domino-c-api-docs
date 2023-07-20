##### Symbolic Value : Log
##### LOG_xxx - Public log flags.
---
```
#include <log.h>
```

**Symbolic Values :**

	LOG_LEAVE_LOCKED	  -  The log entry is not written to disk until it is completed. Can be used with LogAddText, LogAddNumberItem, LogAddTextlistItem, LogAddTimeItem and LogEventExt.

	LOG_AUTO_ROLLOVER	  -  Auto-rollover. Can be used with LogAddText.

	LOG_TO_CONSOLE	  -  Output log entry to console. Can be used with LogAddText.

	LOG_ADD_TIMESTAMP	  -  Add a timestamp to the message. Can be used with LogAddText if the LogEntry parameter is LOG_EVENT_ENTRY and the ItemName parameter is LOG_ITEM_EVENTS.

	LOG_FORMATTED_TEXT	  -  Text is already formatted. Can be used with LogAddText.

	LOG_ITEM_NONSUMMARY	  -  Make the item non summary.


**Description :**

These flags can be used with the LogAdd functions for additional specifications about a log entry.


**See Also :**
[LogAddNumberItem](/domino-c-api-docs/reference/Func/LogAddNumberItem)
[LogAddText](/domino-c-api-docs/reference/Func/LogAddText)
[LogAddTextlistItem](/domino-c-api-docs/reference/Func/LogAddTextlistItem)
[LogAddTimeItem](/domino-c-api-docs/reference/Func/LogAddTimeItem)
---
