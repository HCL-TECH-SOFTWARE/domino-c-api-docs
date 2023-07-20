##### Data Type : IDs
##### NOTEID - Note ID within a database.
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef DWORD NOTEID;
```

**Description :**

A NOTEID identifies a particular note within a given database. Use a NOTEID and a database handle to open a note.<br>
<br>
A NOTEID is a file position that is guaranteed never to change within the database.  It does not contain information about which database the note resides in. The NOTEID does not change when the note is modified. Two replica copies of the same note, in two separate replica databases, will most likely have different NOTEIDs.


**See Also :**
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[ORIGINATORID](/domino-c-api-docs/reference/Data/ORIGINATORID)
[UNIVERSALNOTEID](/domino-c-api-docs/reference/Data/UNIVERSALNOTEID)
---
