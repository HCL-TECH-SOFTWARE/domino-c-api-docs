##### Data Type : Composite Data
##### CDTEXTPROPERTIESTABLE - Text Properties Table.
---
```
#include <editods.h>
```
**Description :**

A field or a run of rich text may contain language information. This language 
information is stored in a $TEXTPROPERTIES item. The start or end of a span of 
language information is indicated by a CDSPANRECORD structure. The 
$TEXTPROPERTIES item and the CDSPANRECORD structures may be stored on a form 
note and/or a document.

A $TEXTPROPERTIES item (also known as a text properties table) is an item of 
TYPE_COMPOSITE which consists of a CDTEXTPROPERTIESTABLE structure, followed by 
a CDTEXTPROPERTY structure for each language present. 

The fields in this record are:

Header -     Signature and Length of this CD record.
NumberOfEntries - Number of CDTEXTPROPERTY records to follow. 

**See Also :**
[CDSPANRECORD](/reference/Data/CDSPANRECORD)
[CDTEXTPROPERTY](/reference/Data/CDTEXTPROPERTY)
---
