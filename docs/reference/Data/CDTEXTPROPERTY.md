##### Data Type : Composite Data
##### CDTEXTPROPERTY - Language information for a field or a run of rich text.
---
```
#include <editods.h>
```
**Description :**

This CD record contains language information for a field or a run of rich text. 
The fields in this record are:

Header - Signature and Length of this CD record.
TextStyleName - Style name if using a named text style, else set to NULL. 
Maximum size is MAX_TEXTSTYLE_NAME.
LangName - Language name information in primary-secondary format, for example: 
"FR-CA" for French Canadian. Maximum size is MAX_ISO_LANG_SIZE.
PropID - Position of language in the text properties table.
Flags - Currently set to zero. 
Reserved2 - Reserved for future use.
Reserved3 - Reserved for future use.
 
A field or a run of rich text may contain language information. This language 
information is stored in a $TEXTPROPERTIES item. The start or end of a span of 
language information is indicated by a CDSPANRECORD structure. The 
$TEXTPROPERTIES item and the CDSPANRECORD structures may be stored on a form 
note and/or a document.

A $TEXTPROPERTIES item (also known as a text properties table) is an item of 
TYPE_COMPOSITE which consists of a CDTEXTPROPERTIESTABLE structure, followed by 
a CDTEXTPROPERTY structure for each language present. 

A CDSPANRECORD record with a SIG_CD_SPAN_BEGIN signature is followed by CD 
records pertaining to either a field or a run of rich text, and a CDSPANRECORD 
record with a SIG_CD_SPAN_END signature.  

A CDTEXTPROPERTIESTABLE NumberOfEntries member reflects the number of 
CDTEXTPROPERTY records to follow. Each of these CDTEXTPROPERTY records' PropID 
member reflects the position of its language in the text properties table. A 
CDSPANRECORD PropID member corresponds to the value of the PropID member of a 
CDTEXTPROPERTY record.

**See Also :**
[CDSPANRECORD](/reference/Data/CDSPANRECORD)
[CDTEXTPROPERTIESTABLE](/reference/Data/CDTEXTPROPERTIESTABLE)
---
