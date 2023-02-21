##### Data Type : HTML
##### HTMLHANDLE - Converter object handle
---
```
#include <htmlapi.h>
```
**Description :**

A converter object is used to access most of the HTML API's features.

**Sample Usage :**
```
HTMLHANDLE cvtr;
rslt = HTMLCreateConverter(&cvtr);
//use this converter to do things you want to do
rslt = HTMLDestroyConverter(cvtr)
```
**See Also :**
[HTMLCreateConverter](/domino-c-api-docs/reference/Func/HTMLCreateConverter)
[HTMLDestroyConverter](/domino-c-api-docs/reference/Func/HTMLDestroyConverter)
---
