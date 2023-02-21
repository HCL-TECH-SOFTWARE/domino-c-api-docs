##### Data Type : Rich Text
##### CDHTMLBEGIN - Start of pass-through HTML text.
---
```
#include <editods.h>
```
**Description :**

Text in a rich-text field can have the "Pass-Thru HTML" attribute.  
Pass-through HTML text is not translated to the Domino rich text format.  
Pass-through HTML text is marked by CDHTMLBEGIN and CDHTMLEND records.

The fields in this structure are:

Header  Identifies this as a CDHTMLBEGIN record.
Spares  Reserved;  must be 0.


**See Also :**
[CDHTMLEND](/domino-c-api-docs/reference/Data/CDHTMLEND)
---
