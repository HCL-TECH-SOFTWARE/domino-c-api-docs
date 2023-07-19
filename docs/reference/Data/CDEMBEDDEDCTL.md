##### Data Type : Composite Data
##### CDEMBEDDEDCTL - Specifies an embedded control window.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;         /* Signature and length of this record. */
   DWORD CtlStyle; 
   WORD  Flags;
   WORD  Width;
   WORD  Height;
   WORD  Version;
   WORD  CtlType;
   WORD  MaxChars;
   WORD  MaxLines;
   WORD  Percentage;
   DWORD Spare[3];
} CDEMBEDDEDCTL;

**Description :**

This CD record may further define attributes within a CDFIELD such as tab order.
<ul><br>
<br>
Header	<br>
CtlStyle		Embedded control Style, see EC_STYLE_xxx<br>
Flags		Embedded control Flags, see EC_FLAG_xxx<br>
Width		Width of embedded control<br>
Height		Height of embedded control<br>
Version		Embedded control version, see EMBEDDEDCTL_VERSIONxxx<br>
CtlType		Embedded control type, see EBMEDDEDCTL_xxx<br>
MaxChars		Maximum Characters<br>
MaxLines		Maximum Lines<br>
Percentage<br>
Spare[3]<br>
</ul>



**See Also :**
[EC_DIALOGUNITS](/domino-c-api-docs/reference/Func/EC_DIALOGUNITS)
[EC_FITTOCONTENTS](/domino-c-api-docs/reference/Func/EC_FITTOCONTENTS)
[EC_FLAG_xxx](/domino-c-api-docs/reference/Symb/EC_FLAG_xxx)
[EC_STYLE_xxx](/domino-c-api-docs/reference/Symb/EC_STYLE_xxx)
[EMBEDDEDCTL_VERSIONxxx](/domino-c-api-docs/reference/Symb/EMBEDDEDCTL_VERSIONxxx)
[EMBEDDEDCTL_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDCTL_xxx)
---
