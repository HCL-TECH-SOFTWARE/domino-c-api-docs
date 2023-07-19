##### Data Type : Composite Data
##### CDFIELDHINT - Record defining a text "hint" associated with a field
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
	WSIG Header;  /* Tag and length */
	WORD HintTextLength;
	WORD Flags;  /* See above */
	WORD Spare;
	DWORD Spare2;
	    /* The 8-bit text string follows... */
} CDFIELDHINT;

**Description :**

The designer of a form may define a &quot;hint&quot; associated with a field. This descriptive text is visible in dimmed text within the field when a document is created using the form and helps the user to know what to select or fill in for the field. This text does not get saved with the document and disappears when the cursor enters the field.  <br>

<ul>If the Flags member is set to FIELDHINT_LIMITED, a CDFIELDHINT record contains hint information for a limited number of object types in a Rich Text Lite field. Rich Text Lite fields are rich text fields in which limits are imposed on the types of objects stored in it.  In addition to object types such as &quot;pictures&quot; or &quot;shared images&quot;, &quot;clear&quot; (to clear the contents of the field) and &quot;help&quot; may be stored.  If the &quot;help&quot; option is selected, the dimmed text within the field will dynamically change to provide a &quot;hint&quot; for the object type selected. For a field with hint information for limited object types, the CDFIELDHINT record may be followed by a CDDATAFLAGS structure. <br>
<br>
The CDFIELDHINT record is preceded by a CDFIELD record. The CDFIELDHINT record is followed by variable length data whose length is specified in the HintTextLength member. This variable length data specifies the field hint. A CDFIELDHINT record may be present for both the field hint and the field limits hint. <br>
<br>
The fields in this record are:<br>
<br>
Header - Signature and Length of this CD record<br>
HintTextLength - Length of the field hint<br>
Flags - see FIELDHINT_xxx<br>
Spare<br>
Spare2<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.</ul>



**See Also :**
[CDDATAFLAGS](/domino-c-api-docs/reference/Data/CDDATAFLAGS)
[CDFIELD](/domino-c-api-docs/reference/Data/CDFIELD)
[FIELDHINT_xxx](/domino-c-api-docs/reference/Symb/FIELDHINT_xxx)
---
