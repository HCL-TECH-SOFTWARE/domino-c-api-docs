##### Symbolic Value : Rich Text
##### FEXT_xxx (Flags1) - CDEXTFIELD - Flags1
---
##### #include <editods.h>
**Description :**
Flags for CDEXTFIELD Flags1.  Note that the low word in Flags1 is not used.

The Keyword Columns sub-field specifies the number of columns to be used when 
displaying the options in a field of type Keyword as either checkboxes or radio 
buttons.  The number of columns ranges from 1 through 8;  the actual field 
value stored is (number of columns) - 1.

The Frame Type subfield specifies the type of background when checkbox or radio 
button keyword fields are displayed.  "None" means no special background is 
displayed.  "Standard" draws an outline around the options.  "3D" draws a 
background as a box with 3-dimensional depth cues.
**See Also :**
[CDEXTFIELD](D:/md_files/CDEXTFIELD.md)
---
