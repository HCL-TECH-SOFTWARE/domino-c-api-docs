##### Data Type : Signal Handler
##### OSSIGBREAKPROC - Function pointer template for Check Break signal handler.
---
```
#include <ossignal.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR OSSIGBREAKPROC)(void);

**Description :**

Definition of a pointer to a function that will handle the Check Break signal.  The default Check Break signal handler returns ERR_CANCEL if the user has issued a Break to interrupt network I/O, and NOERROR otherwise.  This signal handler requires no parameters.


**See Also :**
[IXPostMessage](/domino-c-api-docs/reference/Func/IXPostMessage)
[OSGetSignalHandler](/domino-c-api-docs/reference/Func/OSGetSignalHandler)
[OSSetSignalHandler](/domino-c-api-docs/reference/Func/OSSetSignalHandler)
[OS_SIGNAL_xxx](/domino-c-api-docs/reference/Symb/OS_SIGNAL_xxx)
---
