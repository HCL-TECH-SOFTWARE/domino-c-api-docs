##### Data Type : Rich Text
##### HEAD_DESC_BUFFER - Header/Footer Buffer
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   HEAD_DESC Desc;        /* Header/footer description */
   char String[MAXHEADERSTRING]; /* Buffer for text - 
                                    Must be '\0' terminated */
} HEAD_DESC_BUFFER;

**Description :**

This data structure is passed to Import/Export modules to describe the header or footer for a document.  This structure consists of a HEAD_DESC header followed by an array of type &quot;char&quot; for the header or footer string.<br>
<br>
        Desc            HEAD_DESC structure describing the header or footer<br>
        String            Text for the header or footer


**See Also :**
[EDITEXPORTDATA](/domino-c-api-docs/reference/Data/EDITEXPORTDATA)
[HEAD_DESC](/domino-c-api-docs/reference/Data/HEAD_DESC)
---
