##### Symbolic Value : IDs
##### NOTEID_CATEGORYxxx - Flag in index entry's NOTEID to indicate (ghost) "category entry".
---
```
#include <nif.h>
```

**Symbolic Values :**

	NOTEID_CATEGORY	  -  Bit 31 -> (ghost) "category entry".

	NOTEID_CATEGORY_TOTAL	  -  Bit 31+30 -> (ghost) "grand total entry".

	NOTEID_CATEGORY_INDENT	  -  Bits 24-29 -> category indent level within this column.

	NOTEID_CATEGORY_ID	  -  Low 24 bits are unique category #.


**Description :**

Note: this relies upon the fact that NOTEID_RESERVED is high bit!


**Sample Usage :**
```
/* Print out the list of all the note IDs in this collection. Check
for IDs that indicate a category entry.  These are dummy note IDs
that don't point to a real note. */

      for (i=0; i<notes_found; i++)
          if (!(NOTEID_CATEGORY & id_list[i]))
             printf ("Note ID number %lu is: %lX\n", ++note_count, id_list[i]);
```

**See Also :**
[NOTEID_xxx](/domino-c-api-docs/reference/Symb/NOTEID_xxx)
[NOTEID](/domino-c-api-docs/reference/Data/NOTEID)
---
