##### Data Type : Composite Data
##### CDTEXTPROPERTY - Language information for a field or a run of rich text.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
	WSIG Header;        /* Signature and length of this record */
 char TextStyleName[MAX_TEXTSTYLE_NAME]; /* Text Style Name */
 char LangName[MAX_ISO_LANG_SIZE];     /* Language Tagging information */
 DWORD PropID;
 /* There should be more info here */
 DWORD Flags;
 DWORD Reserved2;
 DWORD Reserved3;
} CDTEXTPROPERTY;

**Description :**

<br>
This CD record contains language information for a field or a run of rich text. The fields in this record are:
<ul></ul>
Header - Signature and Length of this CD record.<br>
TextStyleName - Style name if using a named text style, else set to NULL. Maximum size is MAX_TEXTSTYLE_NAME.<br>
LangName - Language name information in primary-secondary format, for example: &quot;FR-CA&quot; for French Canadian. Maximum size is MAX_ISO_LANG_SIZE.<br>
PropID - Position of language in the text properties table.<br>
Flags - Currently set to zero. <br>
Reserved2 - Reserved for future use.<br>
Reserved3 - Reserved for future use.
<ul> </ul>
A field or a run of rich text may contain language information. This language information is stored in a $TEXTPROPERTIES item. The start or end of a span of language information is indicated by a CDSPANRECORD structure. The $TEXTPROPERTIES item and the CDSPANRECORD structures may be stored on a form note and/or a document.<br>
<br>
A $TEXTPROPERTIES item (also known as a text properties table) is an item of TYPE_COMPOSITE which consists of a CDTEXTPROPERTIESTABLE structure, followed by a CDTEXTPROPERTY structure for each language present. <br>
<br>
A CDSPANRECORD record with a SIG_CD_SPAN_BEGIN signature is followed by CD records pertaining to either a field or a run of rich text, and a CDSPANRECORD record with a SIG_CD_SPAN_END signature.  <br>
<br>
A CDTEXTPROPERTIESTABLE NumberOfEntries member reflects the number of CDTEXTPROPERTY records to follow. Each of these CDTEXTPROPERTY records' PropID member reflects the position of its language in the text properties table. A CDSPANRECORD PropID member corresponds to the value of the PropID member of a CDTEXTPROPERTY record.


**See Also :**
[CDSPANRECORD](/domino-c-api-docs/reference/Data/CDSPANRECORD)
[CDTEXTPROPERTIESTABLE](/domino-c-api-docs/reference/Data/CDTEXTPROPERTIESTABLE)
---
