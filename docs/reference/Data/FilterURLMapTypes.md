##### Data Type : DSAPI
##### FilterURLMapTypes - URL map types
---
```
#include <dsapi.h>
```
**Description :**

This structure is a return value that the filter will have to provide the DSAPI 
layer once the filter determines it needs to handle the kFilterMapURL event. 
The filter is provided with the URL, and if the filter determines it needs to 
do its own mapping, the filter has to provide what kind of mapping, passed via 
this structure, it used to interpret the URL.

**See Also :**
---
