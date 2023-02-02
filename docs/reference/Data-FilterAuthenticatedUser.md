##### Data Type : DSAPI
##### FilterAuthenticatedUser - DSAPI Filter authenticated user structure.
---
##### #include <dsapi.h>
**Description :**
The FilterAuthenticatedUser structure is used by the ServerSupport callback 
functionality of the FilterContext.  see FilterContext for more information

fieldFlags - (Input)  Flags specifying which fields to retrieve.  see 
FilterAuthenticatedUserFields
pUserCannonicalName - (Output)  Set to the cannonical name of an authenticated 
user if fieldFlags contains the value kCannonicalUserName, NULL otherwise.
pWebUserName - (Output)  Set to the web user name if fieldFlags contains the 
value kWebUserName, NULL otherwise.
pUserPassword - (Output)  Set to the web user password if fieldFlags contain 
the value kUserPassword, NULL otherwise.
pUserGroupList - (Output)  Set to the user's group name list if fieldFlags 
contains the value kUserGroupList, NULL otherwise.
**See Also :**
[FilterAuthenticatedUserFields](D:/md_files/FilterAuthenticatedUserFields.md)
[FilterContext](D:/md_files/FilterContext.md)
---
