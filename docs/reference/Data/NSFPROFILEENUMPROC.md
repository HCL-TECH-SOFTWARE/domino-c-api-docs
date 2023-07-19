##### Data Type : Profile Document
##### NSFPROFILEENUMPROC - Callback action routine for NSFProfileEnum.
---
```
#include <nsfnote.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR NSFPROFILEENUMPROC)(
   DBHANDLE hDB, 
   void far *Ctx,
   char *ProfileName,
   WORD ProfileNameLength,
   char *UserName,
   WORD UserNameLength,
   NOTEID ProfileNoteID);

**Description :**

This is the datatype of the action routine passed to NSFProfileEnum.


**See Also :**
[NSFProfileEnum](/domino-c-api-docs/reference/Func/NSFProfileEnum)
---
