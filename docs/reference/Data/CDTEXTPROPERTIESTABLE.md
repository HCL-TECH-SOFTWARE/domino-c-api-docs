##### Data Type : Composite Data
##### CDTEXTPROPERTIESTABLE - Text Properties Table.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
 WSIG Header;
 WORD NumberOfEntries;
} CDTEXTPROPERTIESTABLE;
```

**Description :**

<br>
A field or a run of rich text may contain language information. This language information is stored in a $TEXTPROPERTIES item. The start or end of a span of language information is indicated by a CDSPANRECORD structure. The $TEXTPROPERTIES item and the CDSPANRECORD structures may be stored on a form note and/or a document.<br>
<br>
A $TEXTPROPERTIES item (also known as a text properties table) is an item of TYPE_COMPOSITE which consists of a CDTEXTPROPERTIESTABLE structure, followed by a CDTEXTPROPERTY structure for each language present. <br>
<br>
The fields in this record are:<br>
<br>
Header - 				Signature and Length of this CD record.<br>
NumberOfEntries -	Number of CDTEXTPROPERTY records to follow. 


**See Also :**
[CDSPANRECORD](/domino-c-api-docs/reference/Data/CDSPANRECORD)
[CDTEXTPROPERTY](/domino-c-api-docs/reference/Data/CDTEXTPROPERTY)
---
