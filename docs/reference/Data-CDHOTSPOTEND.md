##### Data Type : Rich Text
##### CDHOTSPOTEND - Specifies the end of a hotspot
---
##### #include <editods.h>
**Description :**
This structure specifies the end of a hot region in a rich text field. There 
are special cases for Release 4.x and Release 5.x hotspot records which have 
either Lotus Script or Release 4.x (or 5.x) actions associated with them.  
These hotspots contain a CDHOTSPOTBEGIN record with the signature 
SIG_CD_V4HOTSPOTBEGIN (or SIG_CD_V5HOTSPOTBEGIN), and a CDHOTSPOTEND record 
with the signature SIG_CD_V4HOTSPOTEND (or SIG_CD_V5HOTSPOTEND).

Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.
**See Also :**
[CDHOTSPOTBEGIN](D:/md_files/CDHOTSPOTBEGIN.md)
---
