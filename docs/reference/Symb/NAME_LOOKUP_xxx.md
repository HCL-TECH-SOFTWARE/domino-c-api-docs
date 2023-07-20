##### Symbolic Value : Address Book
##### NAME_LOOKUP_xxx - Flags to control NAMELookup function
---
```
#include <lookup.h>
```

**Symbolic Values :**

	NAME_LOOKUP_ALL	  -  Return all entries in the view

	NAME_LOOKUP_NOSEARCHING	  -  Only look in first Address book containing desired view for specified names

	NAME_LOOKUP_EXHAUSTIVE	  -  Search ALL Address books, not just the first Address book that contains a match.

	NAME_LOOKUP_UPDATE	  -  Force the namespaces (views) to be made current.


**Description :**

<b>Note:  </b>Address books refer to both the Notes Client Address books, and Domino Directories (the Domino Server Address books).<br>
<br>
       These flags modify the behavior of the NAMELookup() function. Specify any combination of these flags bitwise OR-ed together in the Flags parameter to NAMELookup().<br>
<br>
When Flags is zero, NAMELookup() searches for each specified name in each specified view across all the  Address books in use. It returns information about all the matching names in all the specified views in the first Address book containing a match.<br>
<br>
If the NAME_LOOKUP_ALL bit is set in Flags, NAMELookup() returns information about all the names in each specified view rather than just the specified names. Use this flag to obtain, for example, a list of all the full names of all person records in the $Users view of the first Address book.<br>
<br>
If the NAME_LOOKUP_NOSEARCHING bit is set in Flags, NAMELookup only searches the first Address book containing each desired view. If it does not find a name in the specified view in the first database containing that view, it skips to the next name rather than proceeding to search the next  Address book. Note that this flag does not stop NAMELookup from searching past the first Address book in the list - just the first one containing the desired view.<br>
<br>
If the NAME_LOOKUP_EXHAUSTIVE bit is set in Flags, NAMELookup() returns information about all the matching names in all the specified views in ALL Address books containing a match.<br>
<br>
        If the NAME_LOOKUP_UPDATE bit is set in Flags, NAMELookup() forces updated views.


**See Also :**
[NAMELookup](/domino-c-api-docs/reference/Func/NAMELookup)
---
