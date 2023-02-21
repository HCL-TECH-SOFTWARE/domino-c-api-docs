##### Symbolic Value : Extension Manager
##### CONFLICT_ACTION_xxx - Replication conflict handler return options.
---
```
#include <nsfnote.h>
```
**Description :**

A replication conflict handler is written as an extension manager.  The 
extension manager can pass one of these values back to Domino or Notes in order 
to tell Domino or Notes how to continue.  It can also pass ERR_EM_CONTINUE back 
to Domino or Notes if Domino or Notes is to handle the replication conflict.  
For example, if an error occurs in your replication conflict handler you may 
want to abort handling the conflict yourself and pass ERR_EM_CONTINUE back to 
Domino or Notes.

**See Also :**
[EM_xxx](/domino-c-api-docs/reference/Symb/EM_xxx)
---
