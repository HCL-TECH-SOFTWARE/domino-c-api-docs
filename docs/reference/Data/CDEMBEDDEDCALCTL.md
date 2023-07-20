##### Data Type : Composite Data
##### CDEMBEDDEDCALCTL - Defines properties of an embedded calendar control (date picker).
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
 WSIG   Header;   /* Signature and length of this record. */
 DWORD  Flags;
 COLOR_VALUE HeaderBkgnd;
 COLOR_VALUE SelectionColor;
 WORD  TargetFrameLength;
 DWORD  Spare[10];   /* Reserved for future use - must be zero */  
} CDEMBEDDEDCALCTL;

```

**Description :**

This CD record defines properties of an embedded calendar control (date picker).   It is preceded by CDHOTSPOTBEGIN and CDPLACEHOLDER and is followed by a CDHOTSPOTEND of type HOTSPOTREC_TYPE_EMBEDDEDCALENDARCTL. The fields in this structure are:
<ul><br>
<br>
Header - Signature and length of this record.<br>
Flags - See EMBEDDEDCAL_FLAG_xxx <br>
HeaderBkgnd - Header background color. Set Flags member to EMBEDDEDCAL_FLAG_NON_TRANSPARENT_BKGND.<br>
SelectionColor - Control background color. Set Flags member to EMBEDDEDCAL_FLAG_NON_TRANSPARENT_BKGND.<br>
TargetFrameLength - Target frame length. Set Flags member to EMBEDDEDCAL_FLAG_HASTARGETFRAME.<br>
Spare - Reserved for future use - must be zero.<br>
<br>
These fields may be followed by an optional target frame. If you plan to use it, you will need to declare the variable and assign a value to its length.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.</ul>



**See Also :**
[EMBEDDEDCAL_FLAG_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDCAL_FLAG_xxx)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---
