##### Symbolic Value : Signal Handler
##### OSMESSAGETYPE_xxx - Message signal handler specific definitions.
---
```
#include <ossignal.h>
```

**Symbolic Values :**

	OSMESSAGETYPE_OK	  -  Display a dialog box with an OK pushbutton. The Notes message signal handler will return ERR_OSMESSAGE_OK.

	OSMESSAGETYPE_OKCANCEL	  -  Display a dialog box with OK and CANCEL pushbuttons. The Notes message signal handler will return ERR_OSMESSAGE_OK if the OK button was clicked, ERR_OSMESSAGE_CANCEL if the CANCEL button was clicked.

	OSMESSAGETYPE_YESNO	  -  Display a dialog box with YES and NO pushbuttons. The Notes message signal handler will return ERR_OSMESSAGE_YES if the YES button was clicked, ERR_OSMESSAGE_NO if the NO button was clicked.

	OSMESSAGETYPE_YESNOCANCEL	  -  Display a dialog box with YES, NO, and CANCEL pushbuttons. The Notes message signal handler will return ERR_OSMESSAGE_YES if the YES button was clicked, ERR_OSMESSAGE_NO if the NO button was clicked, ERR_OSMESSAGE_CANCEL if the CANCEL button was clicked.

	OSMESSAGETYPE_RETRYCANCEL	  -  Display a dialog box with RETRY and CANCEL pushbuttons. The Notes message signal handler will return ERR_OSMESSAGE_RETRY if the RETRY button was clicked, ERR_OSMESSAGE_CANCEL if the CANCEL button was clicked.

	OSMESSAGETYPE_POST	  -  Display the server name and a given string in the message/status area of the Notes Status bar. The Notes message signal handler will return ERR_OSMESSAGE_OK.

	OSMESSAGETYPE_POST_NOSERVER	  -  Display a given string in the message/status area of the Notes Status bar. The Notes message signal handler will return ERR_OSMESSAGE_OK.


**Description :**

These symbolic constants define the type of the dialog box to be displayed when a message signal handler function (OS_SIGNAL_MESSAGE) is called.


**See Also :**
[OSSIGMSGPROC](/domino-c-api-docs/reference/Data/OSSIGMSGPROC)
[OS_SIGNAL_xxx](/domino-c-api-docs/reference/Symb/OS_SIGNAL_xxx)
---
