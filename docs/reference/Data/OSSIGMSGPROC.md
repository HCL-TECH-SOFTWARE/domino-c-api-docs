##### Data Type : Signal Handler
##### OSSIGMSGPROC - Function pointer template for Message signal handler.
---
```
#include <ossignal.h>
```
**Description :**

Definition of a pointer to a function that will handle the Message signal.  The 
default Message signal handler displays the text argument in a dialog box with 
pushbuttons determined by the Type parameter.  The return value depends on the 
type of display and user action;  please see the description of the appropriate 
OSMESSAGETYPE_xxx value for the possible return codes.

This signal handler requires two parameters:

    Message - Far pointer to a null-terminated message string to be displayed.

    Type - How the message is to be displayed;  use one of the 
OSMESSAGETYPE_xxx Symbolic Values.

**See Also :**
[DesignRefresh](/reference/Func/DesignRefresh)
[IXPostMessage](/reference/Func/IXPostMessage)
[OSGetSignalHandler](/reference/Func/OSGetSignalHandler)
[OSMESSAGETYPE_xxx](/reference/Symb/OSMESSAGETYPE_xxx)
[OSSetSignalHandler](/reference/Func/OSSetSignalHandler)
[OS_SIGNAL_xxx](/reference/Symb/OS_SIGNAL_xxx)
---
