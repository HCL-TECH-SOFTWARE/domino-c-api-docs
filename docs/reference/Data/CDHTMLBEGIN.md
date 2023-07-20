##### Data Type : Rich Text
##### CDHTMLBEGIN - Start of pass-through HTML text.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;
   BYTE Spares[4];
} CDHTMLBEGIN;
```

**Description :**

Text in a rich-text field can have the &quot;Pass-Thru HTML&quot; attribute.  Pass-through HTML text is not translated to the Domino rich text format.  Pass-through HTML text is marked by CDHTMLBEGIN and CDHTMLEND records.
<ul><br>
<br>
The fields in this structure are:<br>

<ul>Header		Identifies this as a CDHTMLBEGIN record.<br>
Spares		Reserved;  must be 0.</ul>
</ul>



**See Also :**
[CDHTMLEND](/domino-c-api-docs/reference/Data/CDHTMLEND)
---
