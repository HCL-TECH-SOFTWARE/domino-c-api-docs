##### Symbolic Value : Views
##### FIND_xxx - NIFFindByKey(), NIFFindByName() - FindFlags
---
```
#include <nif.h>
```
**Description :**

These flags are used by NIFFindByKey and NIFFindByName to control how the view 
is searched for the key. The flags,  FIND_PARTIAL, FIND_CASE_INSENSITIVE, and 
FIND_ACCENT_INSENSITIVE should only be used for character data, since a 
"partial number" or "partial date" is not well defined.  

The FIND_LESS_THAN and FIND_GREATER_THAN flags refer to the way the sorted 
column keys are ordered and displayed, not the way they compare with each 
other. FIND_LESS_THAN means "find the entry before" and FIND_GREATER_THAN means 
"find the entry after" a desired key.  The FIND_LESS_THAN and FIND_GREATER_THAN 
flags will result in success if at least one key that is less than or greater 
than the specified key, respectively, is found.  

If a FIND_FIRST_EQUAL or FIND_LAST_EQUAL comparison is specified and the number 
of matches is requested to be returned, then the number of entries which match 
the specified key will be returned.  If a FIND_LESS_THAN or FIND_GREATER_THAN 
comparison is specified, then the number of matching entries cannot be 
requested.

**See Also :**
[NIFFindByName](/reference/Func/NIFFindByName)
[NIFFindByKey](/reference/Func/NIFFindByKey)
---
