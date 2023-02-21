##### Data Type : Composite Data
##### CDACTIONEXT - Extended field attributes for CDACTION
---
```
#include <actods.h>
```
**Description :**

New field attributes have been added in Notes/Domino 6.  To preserve 
compatibility with existing applications, the new attributes have been placed 
in this extension to the CDACTION record.  This record is optional, and may not 
be present in the $Body item of the form note.

In R5, a view action's hide whens, and hence state, is only evaluated once when 
the view is loaded. Notes/Domino 6 allows the action's state to be evaluated 
each time a different document becomes current. A checkbox in the action bar 
and/or a checked item on the action menu can change to reflect a value in the 
currently selected document. The control formula value evaluates to true 
(checked) or false (unchecked). The wControlType member of CDACTIONEXT must be 
ACTION_CONTROL_TYPE_CHECKBOX and the view must allow for evaluating actions for 
every document changed . 

The fields in this structure are:

Header - Defines this composite data item as a CDACTIONEXT item.

dwFlags - Reserved for future use.

wControlType - See ACTION_CONTROL_TYPE_xxx.

wControlFormulaLen - Length of formula following this CD record.

wLabelFormulaLen - Length of formula following this CD record. Formula is used 
for control's/menu's label.

wParentLabelFormulaLen - Length of formula following this CD record. 

    wCompActionIDLen - Length of name of action ID (from composite definition). 

    wProgrammaticUseTxtLen - Length of the Program Use attribute

dwExtra - Reserved for future use.

These fields may be followed by an optional control formula value. If you plan 
to use it, you will need to declare the variable and assign a value to its 
length.

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.


**See Also :**
[ACTION_CONTROL_TYPE_xxx](/domino-c-api-docs/reference/Symb/ACTION_CONTROL_TYPE_xxx)
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
