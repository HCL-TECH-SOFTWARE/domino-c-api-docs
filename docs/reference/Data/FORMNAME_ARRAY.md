##### Data Type : Views
##### FORMNAME_ARRAY - Structure of the data block of form names.
---
```
#include <ixview.h>
```

**Definition :**
```
typedef struct {
   /* The following array is intended to be the maximum name length
      for a form.  This used to use DESIGN_NAME_MAX (from names.h)
      but the  value of DESIGN_LEVEL_MAX (which DESIGN_NAME_MAX is derived
      from) was doubled from V3.0 to V3.0J to allow for longer Japanese
      design names.  The hardcoded value below is based on the V3.0 value
      and will allow API programs to be backward and forward compatible.
   */
   char Name[66];
} FORMNAME_ARRAY;
```

**Description :**

VIEWIXDATA, the data structure passed from Notes to view import/export modules, contains a handle to an array of form names (hFormNames).  The handle specifies an array of FORMNAME_ARRAY structures.


**See Also :**
[VIEWIXDATA](/domino-c-api-docs/reference/Data/VIEWIXDATA)
---
