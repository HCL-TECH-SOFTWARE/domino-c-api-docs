##### Symbolic Value : Agents
##### TEXTTERM_FLAG_xxx - Search options for CDQUERYTEXTTERM.
---
```
#include <queryods.h>
```

**Symbolic Values :**

	TEXTTERM_FLAG_RAW	  -  String is a Domino full text search query string.

	TEXTTERM_FLAG_VERITY	  -  String is stored in Verity search engine format.

	TEXTTERM_FLAG_AND	  -  String is comma-separated list of words; AND assumed.

	TEXTTERM_FLAG_ACCRUE	  -  String is comma-separated list of words; ACCRUE assumed.

	TEXTTERM_FLAG_NEAR	  -  String is comma-separated list of words; NEAR assumed.

	TEXTTERM_FLAG_PLAINTEXT	  -  Display this object as plain text.


**Description :**

These option flags may be specified in the dwFlags field of a CDQUERYTEXTTERM record.


**See Also :**
[CDQUERYTEXTTERM](/domino-c-api-docs/reference/Data/CDQUERYTEXTTERM)
---
