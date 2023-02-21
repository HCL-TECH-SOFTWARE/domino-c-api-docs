##### Data Type : Database
##### DBACTIVITY_ENTRY - Database user session activity structure in the array returned from NSFDbGetUserActivity.
---
```
#include <nsfdb.h>
```
**Description :**

This structure is returned by NSFDbGetUserActivity().  This structure holds 
information concerning of the number of documents a user or server read or 
wrote in a database during each session.  NSFDbGetUserActivity() returns an 
array of DBACTIVITY_ENTRY structures followed by a parallel array of 
NULL-terminated user name strings.  Use the NSFDbGetActivityUserNamePtr() macro 
for accessing the user name for each DBACTIVITY_ENTRY structure in the array.

**See Also :**
[DBACTIVITY](/domino-c-api-docs/reference/Data/DBACTIVITY)
[NSFDbGetUserActivity](/domino-c-api-docs/reference/Func/NSFDbGetUserActivity)
[NSFDbGetActivityUserNamePtr](/domino-c-api-docs/reference/Func/NSFDbGetActivityUserNamePtr)
---
