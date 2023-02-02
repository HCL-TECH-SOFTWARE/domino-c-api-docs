##### Data Type : Navigators
##### VIEWMAP_ACTION_RECORD - Navigator action CD record.
---
##### #include <vmods.h>
**Description :**
Identifies an action to be performed from a Navigator.  This record is stored 
in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the Navigator, 
and are paired with Navigator graphic CD records.  The fields in this structure 
are:

Header Defines this composite data item as a VIEWMAP_ACTION_RECORD item.
bHighlightTouch If TRUE:  Highlight when touched.
bHighlightCurrent If TRUE:  Highlight when clicked.
HLOutlineColor Color for are outline.   Use NOTES_COLOR_xxx value.
HLFillColor Fill color for area.   Use NOTES_COLOR_xxx value.
ClickAction Action to perform;  must be a VM_ACTION_xxx value.
ActionStringLen Length of the name of the action to perform, or 0 if not 
applicable; used by VM_ACTION_SWITCH_VIEW, VM_ACTION_SWITCHNAV, and 
VM_ACTION_ALIAS_FOLDER values. 
HLOutlineWidth Line width of area outline.
HLOutlineStyle Style of area outline.   Use VM_LINE_xxx value.
LinkInfo If a note is associated with this action, a link to that note is 
stored in this field, or 0 if not  applicable; used by VM_ACTION_GOTO_LINK 
ClickAction value.   See NOTELINK.
ExtDataLen Length of extended action data, or 0 if not applicable; used by 
VM_ACTION_RUNFORMULA and VM_ACTION_RUNSCRIPT values.
ActionDataDesignType Design type for the object named in the Action String, or 
0 if not applicable; used by VM_ACTION_SWITCH_VIEW, VM_ACTION_SWITCHNAV, and 
VM_ACTION_ALIAS_FOLDER values.  Use DESIGN_TYPE_xxx value.
spare Reserved;  must be 0.

This record is followed by the string containing the name of the action to be 
performed (if any).

**See Also :**
[NOTELINK](D:/md_files/NOTELINK.md)
[VM_ACTION_xxx](D:/md_files/VM_ACTION_xxx.md)
---
