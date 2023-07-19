##### Data Type : DSAPI
##### FilterAuthorize - DSAPI FilterAuthorize structure
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct _FilterAuthorize{
	const char  *pURL; /* Input. The input URL */
	char   *pBuffer; /* Input. The resulting mapping is contained 
	     in the supplied buffer */
	unsigned int bufferSize; /* Size of the buffer supplied */
	unsigned int mapType; /* Mapping type. */
	unsigned int isAuthorized; /* Result of operation, 1 if successful, 0 
otherwise. */
}  FilterAuthorize;

**Description :**

The FilterAuthorize structure is used in the kFilterAuthorized event.  It's described below:<br>

<ul>pURL	- (Input)  The http request URL.<br>
<br>
pBuffer	- (Input)  This buffer contains the path to the target resource.<br>
<br>
bufferSize	- (Input)  The total size in bytes of the supplied buffer.<br>
<br>
mapType	- (Input)  Set to one of the following:
<ul>kURLMapUnknown	- Unknown mapping type.<br>
kURLMapPass	- File system mapping rule<br>
kURLMapExec	- CGI mapping rule<br>
kURLMapRedirect	- Redirect mapping rule<br>
kURLMapService	- (Obsolete). Not used anymore in Notes/Domino 6.<br>
kURLMapDomino	- Domino mapping rule <br>
</ul>
isAuthorized	- (Output)  Set to 1 if the user is granted access to the resource, 0 otherwise.</ul>



**See Also :**
[EventFlags](/domino-c-api-docs/reference/Data/EventFlags)
---
