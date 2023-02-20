##### Data Type : Signal Handler
##### OSSIGBREAKPROC - Function pointer template for Check Break signal handler.
---
```
#include <ossignal.h>
```
**Description :**

Definition of a pointer to a function that will handle the Check Break signal.  
The default Check Break signal handler returns ERR_CANCEL if the user has 
issued a Break to interrupt network I/O, and NOERROR otherwise.  This signal 
handler requires no parameters.

**See Also :**
[IXPostMessage](/reference/Func/IXPostMessage)
[OSGetSignalHandler](/reference/Func/OSGetSignalHandler)
[OSSetSignalHandler](/reference/Func/OSSetSignalHandler)
[OS_SIGNAL_xxx](/reference/Symb/OS_SIGNAL_xxx)
---
