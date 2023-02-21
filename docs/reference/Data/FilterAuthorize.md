##### Data Type : DSAPI
##### FilterAuthorize - DSAPI FilterAuthorize structure
---
```
#include <dsapi.h>
```
**Description :**

The FilterAuthorize structure is used in the kFilterAuthorized event.  It's 
described below:

pURL - (Input)  The http request URL.

pBuffer - (Input)  This buffer contains the path to the target resource.

bufferSize - (Input)  The total size in bytes of the supplied buffer.

mapType - (Input)  Set to one of the following:
kURLMapUnknown - Unknown mapping type.
kURLMapPass - File system mapping rule
kURLMapExec - CGI mapping rule
kURLMapRedirect - Redirect mapping rule
kURLMapService - (Obsolete). Not used anymore in Notes/Domino 6.
kURLMapDomino - Domino mapping rule 

isAuthorized - (Output)  Set to 1 if the user is granted access to the 
resource, 0 otherwise.

**See Also :**
[EventFlags](/domino-c-api-docs/reference/Data/EventFlags)
---
