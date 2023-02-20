##### Data Type : DSAPI
##### FilterInitData - DSAPI Filter initialization entry point prototype.
---
```
#include <dsapi.h>
```
**Description :**

The FilterInitData structure is referenced in the FilterInit entry point 
prototype.  The FilterInit entry point defines the filter initialization.  
Filter initialization is called when the HTTP task loads the filter, which 
occurs as part of the HTTP task startup..  It is also called when the HTTP task 
is restarted with the domino server command "tell http restart".  The filter 
initialization proto type would be defined as follows:

	typedef unsigned int FilterInit( FilterInitData* initData );

FilterInitData Structure:
serverFilterVersion - Input parameter:  The server's version of the filter 
software.
appFilterVersion - Output parameter: The filter's version of the filter 
software.  Set this to kInterfaceVersion.
eventFlags - Output parameter: Indicates for which event the filter wants to be 
called, see EventFlags.
initFlags - not used
filterDesc - Output parameter: a short description of the filter.


**See Also :**
[EventFlags](/reference/Data/EventFlags)
---
