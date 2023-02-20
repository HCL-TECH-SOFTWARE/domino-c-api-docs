##### Data Type : OLE
##### OLE_GUID - On-disk structure of an OLE GUID.
---
```
#include <oleods.h>
```
**Description :**

This is taken directly from OLE's compobj.h.  The reason it's copied rather 
than included here is to eliminate inclusion of the OLE2 header files, which 
without great pain, only compile on OLE platforms.  This header file is 
included on ALL Notes platforms, so we don't want to mess with the whole of OLE 
just for the GUID typedef...

**See Also :**
---
