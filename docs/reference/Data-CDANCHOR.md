##### Data Type : Composite Data
##### CDANCHOR - Target for anchor hotlink.
---
##### #include <editods.h>
**Description :**
An anchor hotlink points to a specific location in a rich text field of a 
document.  That target location is identified by a CDANCHOR record containing a 
specified text string.  When the anchor hotlink is selected by a user, Notes 
displays the anchor location in the target document.  The fields in this record 
are:

Header  Identifies this record as a CDANCHOR record.
Datalength Number of bytes in the anchor text string.
Reserved Must be set to 0.

This record is followed by the anchor text string.
**See Also :**
[CDHOTSPOTBEGIN](D:/md_files/CDHOTSPOTBEGIN.md)
---
