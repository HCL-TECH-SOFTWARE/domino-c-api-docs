##### Data Type : Navigators
##### VIEWMAP_ACTION_RECORD - Navigator action CD record.
---
```
#include <vmods.h>
```

**Definition :**

typedef struct {
   WSIG     Header;
   WORD     bHighlightTouch;
   WORD     bHighlightCurrent;
   WORD     HLOutlineColor;
   WORD     HLFillColor;
   WORD     ClickAction;
   WORD     ActionStringLen;
   WORD     HLOutlineWidth;
   WORD     HLOutlineStyle;
   NOTELINK LinkInfo;
   WORD     ExtDataLen; /* length of extended action data, */
                        /* e.g. compiled script */
   WORD     ActionDataDesignType; /* design type for the named
                                     folder or view named in the
                                     ActionString */
   DWORD    spare[2];   /* reserved for future use */
	 /* Followed by Action Name string */
} VIEWMAP_ACTION_RECORD;

**Description :**

Identifies an action to be performed from a Navigator.  This record is stored in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the Navigator, and are paired with Navigator graphic CD records.  The fields in this structure are:
<ul><br>

<ul>Header	Defines this composite data item as a VIEWMAP_ACTION_RECORD item.<br>
bHighlightTouch	If TRUE:  Highlight when touched.<br>
bHighlightCurrent	If TRUE:  Highlight when clicked.<br>
HLOutlineColor	Color for are outline.   Use NOTES_COLOR_xxx value.<br>
HLFillColor	Fill color for area.   Use NOTES_COLOR_xxx value.<br>
ClickAction	Action to perform;  must be a VM_ACTION_xxx value.<br>
ActionStringLen	Length of the name of the action to perform, or 0 if not applicable; used by VM_ACTION_SWITCH_VIEW, VM_ACTION_SWITCHNAV, and VM_ACTION_ALIAS_FOLDER values. <br>
HLOutlineWidth	Line width of area outline.<br>
HLOutlineStyle	Style of area outline.   Use VM_LINE_xxx value.<br>
LinkInfo	If a note is associated with this action, a link to that note is stored in this field, or 0 if not 	applicable; used by VM_ACTION_GOTO_LINK ClickAction value.   See NOTELINK.<br>
ExtDataLen	Length of extended action data, or 0 if not applicable; used by VM_ACTION_RUNFORMULA and VM_ACTION_RUNSCRIPT values.<br>
ActionDataDesignType	Design type for the object named in the Action String, or 0 if not applicable; used by VM_ACTION_SWITCH_VIEW, VM_ACTION_SWITCHNAV, and VM_ACTION_ALIAS_FOLDER values.  Use DESIGN_TYPE_xxx value.<br>
spare	Reserved;  must be 0.<br>
</ul>
This record is followed by the string containing the name of the action to be performed (if any).</ul>



**See Also :**
[NOTELINK](/domino-c-api-docs/reference/Data/NOTELINK)
[VM_ACTION_xxx](/domino-c-api-docs/reference/Symb/VM_ACTION_xxx)
---
