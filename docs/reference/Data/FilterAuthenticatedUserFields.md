##### Data Type : DSAPI
##### FilterAuthenticatedUserFields - DSAPI filter authenticated user fields structure.
---
```
#include <dsapi.h>
```

**Definition :**

typedef enum{
	kCannonicalUserName  = 0x01,
	kWebUserName  = 0x02,
	kUserPassword  = 0x04,
	kUserGroupList  = 0x08
}FilterAuthenticatedUserFields;

**Description :**

Flags used in the FilterAuthenticatedUser structure<br>

<ul>kCannonicalUserName	- asking for the user authenticated name.<br>
kWebUserName	- asking for the web user's name.<br>
kUserPassword	- asking for the web user's password.<br>
kUserGroupList	- asking for the user's group list.</ul>



**See Also :**
[FilterAuthenticatedUser](/domino-c-api-docs/reference/Data/FilterAuthenticatedUser)
---
