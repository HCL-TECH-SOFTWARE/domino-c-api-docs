##### Data Type : DSAPI
##### FilterURLMapTypes - URL map types
---
```
#include <dsapi.h>
```

**Definition :**

typedef enum {
	kURLMapUnknown = 0,   /* Unknown mapping type. */
	kURLMapPass  = 1,   /* File system mapping rule */
	kURLMapExec  = 2,   /* CGI mapping rule */
	kURLMapRedirect = 3,   /* Redirect mapping rule */
	kURLMapService = 4,   /* Obsolete. Not used anymore in Rnext. */
	kURLMapDomino = 5    /* Domino mapping rule */
} FilterURLMapTypes;

**Description :**

This structure is a return value that the filter will have to provide the DSAPI layer once the filter determines it needs to handle the kFilterMapURL event. The filter is provided with the URL, and if the filter determines it needs to do its own mapping, the filter has to provide what kind of mapping, passed via this structure, it used to interpret the URL.


**See Also :**
---
