##### Data Type : Composite Data
##### CDSPANRECORD - Describes the start or end of a span of language information for a field or a run of rich text. 
---
```
#include <editods.h>
```

**Definition :**

typedef struct
 {
 BSIG Header;  /* Signature and length of this record */
 DWORD PropID; /* Property Number */
 } CDSPANRECORD;


**Description :**

 <br>
This CD Record describes the start or end of a span of language information for a field or a run of rich text. The fields in this record are:<br>
<br>
Header -	Signature and Length of this CD record.<br>
PropID -	Corresponds to the value of the PropID member of a CDTEXTPROPERTY record.<br>
<br>
A field or a run of rich text may contain language information. This language information is stored in a $TEXTPROPERTIES item. The start or end of a span of language information is indicated by a CDSPANRECORD structure. The $TEXTPROPERTIES item and the CDSPANRECORD structures may be stored on a form note and/or a document.<br>
<br>
A $TEXTPROPERTIES item (also known as a text properties table) is an item of TYPE_COMPOSITE which consists of a CDTEXTPROPERTIESTABLE structure, followed by a CDTEXTPROPERTY structure for each language present. <br>
<br>
A CDSPANRECORD record with a SIG_CD_SPAN_BEGIN signature is followed by CD records pertaining to either a field or a run of rich text, and a CDSPANRECORD record with a SIG_CD_SPAN_END signature.  <br>
<br>
A CDTEXTPROPERTIESTABLE NumberOfEntries member reflects the number of CDTEXTPROPERTY records to follow. Each of these CDTEXTPROPERTY records' PropID member reflects the position of its language in the text properties table. A CDSPANRECORD PropID member corresponds to the value of the PropID member of a CDTEXTPROPERTY record.


**See Also :**
[CDTEXTPROPERTIESTABLE](/domino-c-api-docs/reference/Data/CDTEXTPROPERTIESTABLE)
[CDTEXTPROPERTY](/domino-c-api-docs/reference/Data/CDTEXTPROPERTY)
---
