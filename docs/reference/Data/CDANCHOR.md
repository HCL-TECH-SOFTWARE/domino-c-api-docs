##### Data Type : Composite Data
##### CDANCHOR - Target for anchor hotlink.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;     /* Header info */
   WORD  Datalength; /* Length of anchor text string */
   DWORD Reserved; /* Must be 0 */
/* Actual anchor text follows. */
} CDANCHOR;
```

**Description :**

An anchor hotlink points to a specific location in a rich text field of a document.  That target location is identified by a CDANCHOR record containing a specified text string.  When the anchor hotlink is selected by a user, Notes displays the anchor location in the target document.  The fields in this record are:
<ul><br>

<ul>Header		Identifies this record as a CDANCHOR record.<br>
Datalength	Number of bytes in the anchor text string.<br>
Reserved	Must be set to 0.</ul>
<br>
This record is followed by the anchor text string.</ul>



**See Also :**
[CDHOTSPOTBEGIN](/domino-c-api-docs/reference/Data/CDHOTSPOTBEGIN)
---
