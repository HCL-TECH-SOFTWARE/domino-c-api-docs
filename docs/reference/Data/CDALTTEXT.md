##### Data Type : Composite Data
##### CDALTTEXT - Alternate text for HTML Web browsers.
---
```
#include <editods.h>
```
**Description :**

Documents stored on a Lotus Domino server that are viewed via a Web browser may 
contain elements that cannot be displayed by the browser.  These elements may 
have alternate text that the browser will display in their place.  The 
alternate text is stored in a CDALTTEXT record.  The fields in this record are:

Header  Identifies this as a CDALTTEXT record.
wLength Length of the text string, in bytes.
Reserved1 Reserved;  must be 0.

This record is followed by the alternate text string.

**See Also :**
---
