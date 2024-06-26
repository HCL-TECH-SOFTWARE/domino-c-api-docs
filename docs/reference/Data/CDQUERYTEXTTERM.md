##### Data Type : Agents
##### CDQUERYTEXTTERM - Text Search Term query CD record.
---
```
#include <queryods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;
   DWORD dwFlags;                    /* flags for this string */
   DWORD dwLength[MAXTEXTTERMCOUNT]; /* length of strings */
	 /* strings follow */
} CDQUERYTEXTTERM;
```

**Description :**

Text search information is stored in the CDQUERYTEXTTERM record in a field of TYPE_QUERY, usually in the query field of an Agent.  These text strings are used as input to the full text search facility to select the documents to be operated on by the Agent.  This record consists of the structure, followed by up to MAXTEXTTERMCOUNT strings containing the text to search for.  The fields in this structure are:
<ul><br>

<ul>Header	Defines this composite data item as a CDQUERYTEXTTERM item.<br>
dwFlags	Text search flags (see TEXTTERM_FLAG_xxx).<br>
dwLength	Array containing the lengths of the strings;  entries may be 0.</ul>
<br>
This structure is followed by the text strings in packed format (no NUL terminators).</ul>



**See Also :**
[MAXTEXTTERMCOUNT](/domino-c-api-docs/reference/Symb/MAXTEXTTERMCOUNT)
[TEXTTERM_FLAG_xxx](/domino-c-api-docs/reference/Symb/TEXTTERM_FLAG_xxx)
---
