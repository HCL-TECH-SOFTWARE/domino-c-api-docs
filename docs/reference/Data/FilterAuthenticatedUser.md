##### Data Type : DSAPI
##### FilterAuthenticatedUser - DSAPI Filter authenticated user structure.
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct {
	FilterAuthenticatedUserFields  fieldFlags;
	char      *pUserCannonicalName;
	char      *pWebUserName;
	char      *pUserPassword;
	char      *pUserGroupList;
}FilterAuthenticatedUser;

**Description :**

The FilterAuthenticatedUser structure is used by the ServerSupport callback functionality of the FilterContext.  see FilterContext for more information<br>

<ul>fieldFlags	- (Input)  Flags specifying which fields to retrieve.  see FilterAuthenticatedUserFields<br>
pUserCannonicalName	- (Output)  Set to the cannonical name of an authenticated user if fieldFlags contains the value kCannonicalUserName, NULL otherwise.<br>
pWebUserName	- (Output)  Set to the web user name if fieldFlags contains the value kWebUserName, NULL otherwise.<br>
pUserPassword	- (Output)  Set to the web user password if fieldFlags contain the value kUserPassword, NULL otherwise.<br>
pUserGroupList	- (Output)  Set to the user's group name list if fieldFlags contains the value kUserGroupList, NULL otherwise.</ul>



**See Also :**
[FilterAuthenticatedUserFields](/domino-c-api-docs/reference/Data/FilterAuthenticatedUserFields)
[FilterContext](/domino-c-api-docs/reference/Data/FilterContext)
---
