##### Data Type : Access Control List
##### NAMES_LIST - User names list structure
---
```
#include <acl.h>
```

**Definition :**

typedef struct {
   WORD        NumNames;      /* Number of names in list */
   LICENSEID   License;       /* User's license - now obsolete */
                              /* MUST BE ZERO. */
   #if defined(UNIX) || defined(OS2_2x) || defined(W32)
   DWORD       Authenticated; /* Authentication flags */
   #else       
   WORD        Authenticated;
   #endif

/* Names follow as packed null-terminated strings. First name is Username.
   Subsequent names are ALL the group names that User is a member
   of (directly or indirectly). */
} NAMES_LIST;

**Description :**

Contains information used by ACLLookupAccess to look up the access level of the user associated with this strucuture.<br>

<ul>See NAMES_LIST_xxx for posiible values for the Authenticated member of this structure.</ul>



**See Also :**
[ACLLookupAccess](/domino-c-api-docs/reference/Func/ACLLookupAccess)
[NAMES_LIST_xxx](/domino-c-api-docs/reference/Symb/NAMES_LIST_xxx)
---
