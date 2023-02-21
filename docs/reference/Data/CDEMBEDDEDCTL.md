##### Data Type : Composite Data
##### CDEMBEDDEDCTL - Specifies an embedded control window.
---
```
#include <editods.h>
```
**Description :**

This CD record may further define attributes within a CDFIELD such as tab order.

Header 
CtlStyle  Embedded control Style, see EC_STYLE_xxx
Flags  Embedded control Flags, see EC_FLAG_xxx
Width  Width of embedded control
Height  Height of embedded control
Version  Embedded control version, see EMBEDDEDCTL_VERSIONxxx
CtlType  Embedded control type, see EBMEDDEDCTL_xxx
MaxChars  Maximum Characters
MaxLines  Maximum Lines
Percentage
Spare[3]



**See Also :**
[EC_DIALOGUNITS](/domino-c-api-docs/reference/Func/EC_DIALOGUNITS)
[EC_FITTOCONTENTS](/domino-c-api-docs/reference/Func/EC_FITTOCONTENTS)
[EC_FLAG_xxx](/domino-c-api-docs/reference/Symb/EC_FLAG_xxx)
[EC_STYLE_xxx](/domino-c-api-docs/reference/Symb/EC_STYLE_xxx)
[EMBEDDEDCTL_VERSIONxxx](/domino-c-api-docs/reference/Symb/EMBEDDEDCTL_VERSIONxxx)
[EMBEDDEDCTL_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDCTL_xxx)
---
