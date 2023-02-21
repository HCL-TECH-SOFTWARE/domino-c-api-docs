##### Symbolic Value : Access Control List
##### ACL_FLAG_xxx - Access level modifier flags.
---
```
#include <acl.h>
```
**Description :**

These symbols represent access level modifier flags in access control lists.  
Each access level taken by itself implies a certain set of immutable 
capabilities. Each access level has a different set of access modifier bits 
that are relevant for that level.  All of the other bits that are returned in 
the Access Flag parameter of C API functions are irrelevant and are 
unpredictable. The table below depicts which Access Level Modifier Flags 
(ACL_FLAG_xxx) are applicable to the Access Levels (ACL_LEVEL_xxx).


ACL_LEVEL_xxx	ACL_FLAG_xxx Applicable 
	to ACL_LEVEL_xxx
ACL_LEVEL_MANAGER	ACL_FLAG_NODELETE
	ACL_FLAG_PERSON
	ACL_FLAG_GROUP
	ACL_FLAG_SERVER
ACL_LEVEL_DESIGNER	ACL_FLAG_NODELETE
	ACL_FLAG_CREATE_LOTUSSCRIPT
	ACL_FLAG_PERSON
	ACL_FLAG_GROUP
	ACL_FLAG_SERVER
ACL_LEVEL_EDITOR	ACL_FLAG_NODELETE
	ACL_FLAG_CREATE_PRAGENT
	ACL_FLAG_CREATE_PRFOLDER
	ACL_FLAG_CREATE_FOLDER
	ACL_FLAG_CREATE_LOTUSSCRIPT
	ACL_FLAG_PERSON
	ACL_FLAG_GROUP
	ACL_FLAG_SERVER
ACL_LEVEL_AUTHOR	ACL_FLAG_AUTHOR_NOCREATE
	ACL_FLAG_NODELETE
	ACL_FLAG_CREATE_PRAGENT
	ACL_FLAG_CREATE_PRFOLDER
	ACL_FLAG_CREATE_LOTUSSCRIPT
	ACL_FLAG_PUBLICWRITER
	ACL_FLAG_PERSON
	ACL_FLAG_GROUP
	ACL_FLAG_SERVER
ACL_LEVEL_READER	ACL_FLAG_CREATE_PRAGENT
	ACL_FLAG_CREATE_PRFOLDER
	ACL_FLAG_CREATE_LOTUSSCRIPT
	ACL_FLAG_PUBLICWRITER
	ACL_FLAG_PERSON
	ACL_FLAG_GROUP
	ACL_FLAG_SERVER
ACL_LEVEL_DEPOSITOR	ACL_FLAG_PUBLICREADER
	ACL_FLAG_PUBLICWRITER
	ACL_FLAG_PERSON
	ACL_FLAG_GROUP
	ACL_FLAG_SERVER
ACL_LEVEL_NOACCESS	ACL_FLAG_PUBLICREADER
	ACL_FLAG_PUBLICWRITER
	ACL_FLAG_PERSON
	ACL_FLAG_GROUP
	ACL_FLAG_SERVER


**See Also :**
[ACLLookupAccess](/domino-c-api-docs/reference/Func/ACLLookupAccess)
[ACLAddEntry](/domino-c-api-docs/reference/Func/ACLAddEntry)
[ACLUpdateEntry](/domino-c-api-docs/reference/Func/ACLUpdateEntry)
[ACLEnumEntries](/domino-c-api-docs/reference/Func/ACLEnumEntries)
[NSFDbAccessGet](/domino-c-api-docs/reference/Func/NSFDbAccessGet)
---
