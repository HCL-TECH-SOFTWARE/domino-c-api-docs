##### Symbolic Value : Mail Gateway
##### MAIL_LOG_xxx - Mail event logging flags.
---
```
#include <mailserv.h>
```

**Symbolic Values :**

	MAIL_LOG_TO_MISCEVENTS	  -  Log message to Miscellaneous Events view.

	MAIL_LOG_TO_MAILEVENTS	  -  Log message to Mail Events view.

	MAIL_LOG_TO_EVENTS_ONLY	  -  Don't log messages to console.

	MAIL_LOG_TO_BOTH	  -  Log message to both Miscellaneous Events and Mail Events views.

	MAIL_LOG_FORMATTED_TEXT	  -  Text already formatted


**Description :**

Flags that can be used in MailLogEvent and MailLogEventText to control mail logging.


**See Also :**
[MailLogEvent](/domino-c-api-docs/reference/Func/MailLogEvent)
[MailLogEventText](/domino-c-api-docs/reference/Func/MailLogEventText)
---
