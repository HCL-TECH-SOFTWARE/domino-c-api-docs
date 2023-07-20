##### Data Type : Signal Handler
##### OSSIGMSGPROC - Function pointer template for Message signal handler.
---
```
#include <ossignal.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR OSSIGMSGPROC)(
   char far * Message,
   WORD       Type);
```

**Description :**

Definition of a pointer to a function that will handle the Message signal.  The default Message signal handler displays the text argument in a dialog box with pushbuttons determined by the Type parameter.  The return value depends on the type of display and user action;  please see the description of the appropriate OSMESSAGETYPE_xxx value for the possible return codes.<br>
<br>
This signal handler requires two parameters:<br>
<br>
    Message - Far pointer to a null-terminated message string to be displayed.<br>
<br>
    Type - How the message is to be displayed;  use one of the OSMESSAGETYPE_xxx Symbolic Values.


**See Also :**
[DesignRefresh](/domino-c-api-docs/reference/Func/DesignRefresh)
[IXPostMessage](/domino-c-api-docs/reference/Func/IXPostMessage)
[OSGetSignalHandler](/domino-c-api-docs/reference/Func/OSGetSignalHandler)
[OSMESSAGETYPE_xxx](/domino-c-api-docs/reference/Symb/OSMESSAGETYPE_xxx)
[OSSetSignalHandler](/domino-c-api-docs/reference/Func/OSSetSignalHandler)
[OS_SIGNAL_xxx](/domino-c-api-docs/reference/Symb/OS_SIGNAL_xxx)
---
