##### Data Type : Administration Process
##### AdminpAddInMessage - Administration process message queue message structure.
---
```
#include <adminp.h>
```

**Definition :**

typedef struct {
   NOTEID RequestNoteId; 
   NOTEID ResponseNoteId;
} AdminpAddInMessage;

**Description :**

This is the structure of a message in the administrative process message queue.


**See Also :**
---
