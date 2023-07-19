##### Data Type : Composite Data
##### CDDATAFLAGS - Collapsible section, button type, style sheet or field limit information for Notes/Domino 6.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
 BSIG Header;
 WORD nFlags;  /* number of flags */
 WORD elemType;  /* element these flags are for, CD_xxx_ELEMENT */
 DWORD dwReserved;  /* future */
 /* DWORDS of flags follow... */
} CDDATAFLAGS;


**Description :**

Contains collapsible section, button type, style sheet or field limit information for Notes/Domino 6. A CD record (CDBAR, CDBUTTON, CDBORDERINFO, CDFIELDHINT, etc.) may be followed by a CDDATAFLAGS structure. 
<ul><br>
<br>
The fields in this structure are:<br>
<br>
Header - Defines this composite data item as a CDDATAFLAGS item.<br>
<br>
nFlags - Number of flags.  <br>
<br>
elemType - CD_SECTION_ELEMENT, CD_BUTTONEX_ELEMENT or CD_FIELDLIMIT_ELEMENT<br>
<br>
dwReserved - Future use.<br>
<br>
If the value of the nFlags member is greater than zero, then immediately following this structure there will be n DWORD Flags that identify the value of the Flags data border, button type, style sheet or field limit.  You can use the macros GETDATABORDERTYPE and SETDATABORDERTYPE to get and set each of the Flags.<br>
</ul>
   If elemType is CD_FIELDLIMIT_ELEMENT, you can use Flag &amp; FIELD_LIMIT_TYPE_XXX is not zero to get the limit type.  See FIELD_LIMIT_TYPE_XXX.
<ul><br>
Note that CDDATAFLAGS records reside in items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on structures of this type when accessing these records in an item in a note.</ul>



**See Also :**
[BARREC_DATA_BORDER_xxx](/domino-c-api-docs/reference/Symb/BARREC_DATA_BORDER_xxx)
[BUTTON_TYPE_xxx](/domino-c-api-docs/reference/Symb/BUTTON_TYPE_xxx)
[CDBAR](/domino-c-api-docs/reference/Data/CDBAR)
[CDBUTTON](/domino-c-api-docs/reference/Data/CDBUTTON)
[CDFIELDHINT](/domino-c-api-docs/reference/Data/CDFIELDHINT)
[CD_xxx_ELEMENT](/domino-c-api-docs/reference/Symb/CD_xxx_ELEMENT)
[GETDATABORDERTYPE](/domino-c-api-docs/reference/Func/GETDATABORDERTYPE)
[SETDATABORDERTYPE](/domino-c-api-docs/reference/Func/SETDATABORDERTYPE)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---
