##### Symbolic Value : Address Book
##### NAME_xxx - Options for function NAMEGetAddressBooks().
---
```
#include <lookup.h>
```

**Symbolic Values :**

	NAME_GET_AB_TITLES	  -  Add the title of the database to each entry in the buffer returned by NAMEGetAddressBooks.

	NAME_DEFAULT_TITLES	  -  If NAME_GET_AB_TITLES is specified then return the database path in place of the title for any database that has no title. NAME_DEFAULT_TITLES has no effect if NAME_GET_AB_TITLES is not also specified.

	NAME_GET_AB_FIRSTONLY	  -  Return only the first Address book in use locally or Domino Directory on a server.

	NAME_GET_MAB_ONLY	  -  Return only the name of the Directory Assistance Database.

	NAME_GET_ED_ONLY	  -  Get server based Enterprise Directory name only.

	NAME_INCLUDE_ED	  -  Include server based Enterprise Directory as the last Domino Directory.

	NAME_GET_ALL_EDS	  -  Get All enterprise Directories.

	NAME_ADMIN_ONLY	  -  Include only NAB's that this server is the administration server of.

	NAME_INCLUDE_CONFIGNAB	  -  Include Configuration (userless) NAB's.

	NAME_CONFIG_ONLY	  -  Include First AB that has configuration information.


**Description :**

These flags modify the behavior of function NAMEGetAddressBooks(). The wOptions parameter to NAMEGetAddressBooks may be zero or any combination of these flags bitwise  OR'd together.<br>
<br>
If none of these flags are set in the wOptions parameter to NAMEGetAddresssBooks, then the buffer returned contains a list of Address Book database file paths.


**See Also :**
[NAMEGetAddressBooks](/domino-c-api-docs/reference/Func/NAMEGetAddressBooks)
[OSPathNetParse](/domino-c-api-docs/reference/Func/OSPathNetParse)
---
