##### Data Type : Views
##### FULLFORMNAME - Structure of the data block of complete (synonyms included) form names.
---
```
#include <ixview.h>
```

**Definition :**

typedef struct {
   char FullName[FULLNAME_SIZE];
} FULLFORMNAME;

**Description :**

VIEWIXDATA, the data structure passed from Notes to view import/export modules, contains a handle to an array of full form names that include include synonyms (hFormNamesFull).  The handle specifies an array of FULLFORMNAME structures.


**See Also :**
[VIEWIXDATA](/domino-c-api-docs/reference/Data/VIEWIXDATA)
---
