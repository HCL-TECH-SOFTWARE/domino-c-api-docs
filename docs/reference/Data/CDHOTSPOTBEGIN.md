##### Data Type : Composite Data
##### CDHOTSPOTBEGIN - Specifies the start of a hotspot.
---
```
#include <editods.h>
```
**Description :**

This structure specifies the start of a "hot" region in a rich text field.  
Clicking on a hot region causes some other action to occur.  For instance, 
clicking on a popup will cause a block of text associated with that popup to be 
displayed.

Normally, each CDHOTSPOTBEGIN record is followed by records describing the 
hotspot and any associated action formula and, finally, a CDHOTSPOTEND record.  
There are special cases for Release 4.x, Release 5.x and 6 hotspot records 
which have either Lotus Script or Release 4.x (or 5.x or 6) actions associated 
with them.  These hotspots contain a CDHOTSPOTBEGIN record with the signature 
SIG_CD_V4HOTSPOTBEGIN (or SIG_CD_V5HOTSPOTBEGIN or 
SIG_CD_V6HOTSPOTBEGIN_CONTINUATION), and a CDHOTSPOTEND record with the 
signature SIG_CD_V4HOTSPOTEND (or SIG_CD_V5HOTSPOTEND).

The fields in this record are:

  Header:     Defines this composite data item as a
              CDHOTSPOTBEGIN item.
  Type:       Specifies the type of hotspot.
              See HOTSPOTREC_TYPE_xxx.
  Flags:      Defines some of the hotspot's attributes.
              See HOTSPOTREC_RUNFLAG_xxx
  DataLength: Specifies the length of the variable-length
              data for this item.

The above fields are then followed by some variable length data, the format of 
which is dependent on the type of hotspot that is being defined.  The variable 
length data for the different hotspot types is as follows:

If the Type is HOTSPOTREC_TYPE_POPUP and the  HOTSPOTREC_RUNFLAG_FORMULA flag 
is not set, then the variable-length data is a packed string containing the 
popup's static text.
If the Type is HOTSPOTREC_TYPE_POPUP and the  HOTSPOTREC_RUNFLAG_FORMULA flag 
is set, then the variable-length data is the compiled formula that will 
generate the popup's text.
If theType is HOTSPOTREC_TYPE_BUTTON then the variable-length data is the 
button's compiled formula.
If the Type is HOTSPOTREC_TYPE_FILE then the variable-length data consists of 
two null-terminated strings. The first string is the internal unique file name 
assigned to the attached file by Domino or Notes. The second string is the 
original name of the file.
If the Type is HOTSPOTREC_TYPE_HOTLINK and the HOTSPOTREC_RUNFLAG_INOTES flag 
is set, then the variable-length data is a packed string containing the URL's 
static text.
If the flag HOTSPOTREC_RUNFLAG_SIGNED is set, the variable-length data 
determined by the hotspot type and other flags is followed by a WORD containing 
the length of the digital signature, then the digital signature for the hotspot.

Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.

**See Also :**
[CDHOTSPOTEND](/domino-c-api-docs/reference/Data/CDHOTSPOTEND)
[HOTSPOTREC_TYPE_xxx](/domino-c-api-docs/reference/Symb/HOTSPOTREC_TYPE_xxx)
[HOTSPOTREC_RUNFLAG_xxx](/domino-c-api-docs/reference/Symb/HOTSPOTREC_RUNFLAG_xxx)
---
