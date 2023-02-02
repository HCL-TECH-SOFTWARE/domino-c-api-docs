##### Data Type : Composite Data
##### CDEMBEDDEDCALCTL - Defines properties of an embedded calendar control (date picker).
---
##### #include <editods.h>
**Description :**
This CD record defines properties of an embedded calendar control (date 
picker).   It is preceded by CDHOTSPOTBEGIN and CDPLACEHOLDER and is followed 
by a CDHOTSPOTEND of type HOTSPOTREC_TYPE_EMBEDDEDCALENDARCTL. The fields in 
this structure are:

Header - Signature and length of this record.
Flags - See EMBEDDEDCAL_FLAG_xxx 
HeaderBkgnd - Header background color. Set Flags member to 
EMBEDDEDCAL_FLAG_NON_TRANSPARENT_BKGND.
SelectionColor - Control background color. Set Flags member to 
EMBEDDEDCAL_FLAG_NON_TRANSPARENT_BKGND.
TargetFrameLength - Target frame length. Set Flags member to 
EMBEDDEDCAL_FLAG_HASTARGETFRAME.
Spare - Reserved for future use - must be zero.

These fields may be followed by an optional target frame. If you plan to use 
it, you will need to declare the variable and assign a value to its length.

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.
**See Also :**
[EMBEDDEDCAL_FLAG_xxx](D:/md_files/EMBEDDEDCAL_FLAG_xxx.md)
[SIG_CD_xxx](D:/md_files/SIG_CD_xxx.md)
---
