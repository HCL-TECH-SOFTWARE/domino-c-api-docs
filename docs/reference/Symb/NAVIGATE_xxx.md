##### Symbolic Value : Views
##### NAVIGATE_xxx - How NIFReadEntries steps through a collection.
---
```
#include <nif.h>
```
**Description :**

These flags control how NIFReadEntries steps through a collection. The flags 
are used to control both the order in which NIFReadEntries skips notes in a 
collection before reading any notes, and navigates the collection while it is 
being read.

The minlevel and/or maxlevel navigation criteria will be used if the 
NAVIGATE_MINLEVEL and/or NAVIGATE_MAXLEVEL navigation flags are set in either 
the SkipNavigator or ReturnNavigator parameters to NIFReadEntries.  Regardless 
of which parameter these flags are set in, if the flags are set in either one 
of these parameters the flags will affect the collection levels that are used 
in both skip navigation and return navigation of the collection.

**See Also :**
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
