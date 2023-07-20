##### Symbolic Value : Views
##### FIND_xxx - NIFFindByKey(), NIFFindByName() - FindFlags
---
```
#include <nif.h>
```

**Symbolic Values :**

	FIND_PARTIAL	  -  Match only the initial characters ("T" matches "Tim", "i" does not match "Tim"). If multiple keys are used, a partial match is done on each of the keys in the order that they are specified. A partial match must be found for all specified keys in order for a particular entry to be considered a successful match.

	FIND_CASE_INSENSITIVE	  -  Case insensitive matching ("tim" matches "Tim").

	FIND_RETURN_DWORD	  -  Return up to MAXDWORD number of matching notes. If not specified, return up to MAXWORD number of matching notes.

	FIND_ACCENT_INSENTIVE	  -  Search disregards diacritical marks.

	FIND_UPDATE_IF_NOT_FOUND	  -  If key is not found, update collection and search again.

	FIND_LESS_THAN	  -  Find last entry less than the key value. (Specify no more than one of: FIND_LESS_THAN, FIND_FIRST_EQUAL, FIND_LAST_EQUAL, FIND_GREATER_THAN)

	FIND_FIRST_EQUAL	  -  Find first entry equal to the key value (if more than one). This flag is the default. (Specify no more than one of: FIND_LESS_THAN, FIND_FIRST_EQUAL, FIND_LAST_EQUAL, FIND_GREATER_THAN)

	FIND_LAST_EQUAL	  -  Find last entry equal to the key value (if more than one). (Specify no more than one of: FIND_LESS_THAN, FIND_FIRST_EQUAL, FIND_LAST_EQUAL, FIND_GREATER_THAN)

	FIND_GREATER_THAN	  -  Find first entry greater than the key value. (Specify no more than one of: FIND_LESS_THAN, FIND_FIRST_EQUAL, FIND_LAST_EQUAL, FIND_GREATER_THAN)

	FIND_EQUAL	  -  Qualifies LESS_THAN and GREATER_THAN to mean LESS_THAN_OR_EQUAL and GREATER_THAN_OR_EQUAL

	FIND_COMPARE_MASK	  -  Bitmask of FIND_LESS_THAN, FIND_FIRST_EQUAL, FIND_LAST_EQUAL, FIND_GREATER_THAN, FIND_EQUAL comparison flags.

	FIND_RANGE_OVERLAP	  -  Overlapping ranges match, and values within a range match. This symbol is valid for fields of type TYPE_TIME_RANGE and TYPE_NUMBER_RANGE. Therefore it should only be used with NIFFindByKey.

	FIND_RETURN_ANY_NON_CATEGORY_MATCH	  -  Return any entry representing an actual document (a non-category entry), instead of searching for the first (or last) entry in the category. It is unpredictable exactly which entry you will get. A count of the matched document and any subsequent documents that match is returned. This count may be less than the actual number of documents that match.

	FIND_NONCATEGORY_ONLY	  -  Only match non-category entries.


**Description :**

These flags are used by NIFFindByKey and NIFFindByName to control how the view is searched for the key. The flags,  FIND_PARTIAL, FIND_CASE_INSENSITIVE, and FIND_ACCENT_INSENSITIVE should only be used for character data, since a &quot;partial number&quot; or &quot;partial date&quot; is not well defined.  <br>

<ul>The FIND_LESS_THAN and FIND_GREATER_THAN flags refer to the way the sorted column keys are ordered and displayed, not the way they compare with each other. FIND_LESS_THAN means &quot;find the entry before&quot; and FIND_GREATER_THAN means &quot;find the entry after&quot; a desired key.  The FIND_LESS_THAN and FIND_GREATER_THAN flags will result in success if at least one key that is less than or greater than the specified key, respectively, is found.  <br>
<br>
If a FIND_FIRST_EQUAL or FIND_LAST_EQUAL comparison is specified and the number of matches is requested to be returned, then the number of entries which match the specified key will be returned.  If a FIND_LESS_THAN or FIND_GREATER_THAN comparison is specified, then the number of matching entries cannot be requested.</ul>



**See Also :**
[NIFFindByName](/domino-c-api-docs/reference/Func/NIFFindByName)
[NIFFindByKey](/domino-c-api-docs/reference/Func/NIFFindByKey)
---
