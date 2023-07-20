##### Data Type : Composite Data
##### CDTEXTEFFECT - Special effect font setting for rich text.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG   Header;       /* Tag and length */
   FONTID FontEffectID; /* Font ID */
} CDTEXTEFFECT;
```

**Description :**

The CDTEXTEFFECT record stores a &quot;special effect&quot; font ID for a run of rich text.  The fields in this record are:
<ul><br>

<ul>
<ul>Header	Defines this composite data item as a CDTEXTEFFECT item.<br>
FontEffectID	Font ID of the special effect font (see FONTID).</ul>
</ul>
</ul>



**See Also :**
[CDTEXT](/domino-c-api-docs/reference/Data/CDTEXT)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
---
