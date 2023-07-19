##### Data Type : DSAPI
##### FilterInitData - DSAPI Filter initialization entry point prototype.
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct {
   unsigned int   serverFilterVersion;
   unsigned int   appFilterVersion;
   unsigned int   eventFlags;
   unsigned int   initFlags;
   char           filterDesc[kMaxFilterDesc+1];
} FilterInitData;

**Description :**


<ul><br>
The FilterInitData structure is referenced in the FilterInit entry point prototype.  The FilterInit entry point defines the filter initialization.  Filter initialization is called when the HTTP task loads the filter, which occurs as part of the HTTP task startup..  It is also called when the HTTP task is restarted with the domino server command &quot;tell http restart&quot;.  The filter initialization proto type would be defined as follows:<br>
<br>
	typedef unsigned int FilterInit( FilterInitData* initData );<br>
<br>
FilterInitData Structure:<br>
serverFilterVersion	- Input parameter: 	The server's version of the filter software.<br>
appFilterVersion	- Output parameter:	The filter's version of the filter software.  Set this to kInterfaceVersion.<br>
eventFlags	- Output parameter:	Indicates for which event the filter wants to be called, see EventFlags.<br>
initFlags	- not used<br>
filterDesc	- Output parameter:	a short description of the filter.</ul>



**See Also :**
[EventFlags](/domino-c-api-docs/reference/Data/EventFlags)
---
