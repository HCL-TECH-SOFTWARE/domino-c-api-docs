##### Symbolic Value : Database
##### NSF_INFO_SIZE - Maximum length for thedatabase information buffer of a Domino database.
---
```
#include <nsfdb.h>
```
**Description :**

This is the maximum length for the database information buffer of a Domino 
database.  This buffer is defined to contain text in host format that is 
null-terminated.  This is the ONLY null-terminated field in all of NSF.  The 
database information buffer contains one or more of the following pieces of 
information:  database title, categories, class, and design class.

**See Also :**
[NSFDbInfoGet](/reference/Func/NSFDbInfoGet)
[NSFDbInfoModify](/reference/Func/NSFDbInfoModify)
[NSFDbInfoParse](/reference/Func/NSFDbInfoParse)
[NSFDbInfoSet](/reference/Func/NSFDbInfoSet)
---
