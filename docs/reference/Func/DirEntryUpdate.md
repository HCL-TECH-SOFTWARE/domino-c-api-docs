##### Function : Dir
##### DirEntryUpdate - Update the in-memory  hEntry object to the directory, committing all the changes that have been made.
---
```
#include <direntry.h>
STATUS LNPUBLIC DirEntryUpdate(

	DIRENTRY  hEntry);
```
**Description :**

If the hEntry was just created with a DirCtxCreateDominoPerson() operation and 
the specified domainName is a Domino directory, then a new entry is created 
with the specified DN. If it is an LDAP directory then a new entry is created 
with the specified distinguishedName and notesDNs If an entry by the same DN or 
notesDN exists in the relevant directory then an error is returned. 
        On return all changes queued up in the hEntry by item add, delete, 
replace operations are cleared so the caller is free to use the same hEntry to 
make further changes.

**Parameters :**
Input :
hEntry  -  Handle to the person entry to update.

Output :
(routine)  -  An ERR status on failure indicating the problem. 



**See Also :**
[DirEntryItemAdd](/domino-c-api-docs/reference/Func/DirEntryItemAdd)
[DirEntryItemDelete](/domino-c-api-docs/reference/Func/DirEntryItemDelete)
---
