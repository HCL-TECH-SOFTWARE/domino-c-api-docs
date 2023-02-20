##### Data Type : Composite Data
##### CDEMBEDDEDSCHEDCTLEXTRA - Extended field attributes for CDEMBEDDEDSCHEDCTL.
---
```
#include <editods.h>
```
**Description :**

New field attributes have been added in Notes/Domino 6.  To preserve 
compatibility with existing applications, the new attributes have been placed 
in this extension to the CDEMBEDDEDSCHEDCTL record.  This record is optional, 
and may not be present in the $Body item of the form note.

The fields in this structure are:

Header - Signature and length of this CD record
FixedPartLength - Length in bytes of this structure
Flags - See EMBEDDEDSCHEDEXT_FLAG_xxx
SchedHdrBkgndColor - Background color of scheduler headers
SchedHdrFontColor - Font color of scheduler headers
SchedBkgndColor - Background color of scheduler 
NameHdrBkgndColor - Background color of name header area 
NameHdrFontColor - Font color of name header area
NameBkgndColor - Normal background color of attendee names
NameMouseBkgndColor - Mouse over background color of attendee names
NameSelectBkgndColor - Select background color of attendee names
NameFontColor - Normal font color of attendee names
NameMouseFontColor - Mouse over font color of attendee names
NameSelectFontColor - Select font color of attendee names
OptPeopleItemsFormulaLength - Length of optional people items formula, value 
follows CD fixed portion
ReqRoomsItemsFormulaLength - Length of required rooms items formula, value 
follows CD fixed portion
OptRoomsItemsFormulaLength - Length of optional rooms items formula, value 
follows CD fixed portion
ReqResourcesItemsFormulaLength - Length of required resources items formula, 
value follows CD fixed portion
OptResourcesItemsFormulaLength - Length of optional resources items formula, 
value follows CD fixed portion
IntervalStartDTItemFormulaLength - Length of interval start date time item 
formula, value follows CD fixed portion
IntervalEndDTItemFormulaLength - Length of interval end date time item formula, 
value follows CD fixed portion
SchedulerNameLength - Length of scheduler name, value follows CD fixed portion
PeopleTitleLength - Length of people title, values follows CD fixed portion
RoomsTitleLength - Length of rooms title, values follows CD fixed portion
ResourcesTitleLength - Length of resources title, value follows CD fixed portion
IntervalChangeEventFormulaLength - Length of interval change event formula, 
value follows CD fixed portion
ProfileColor - Color used to paint busy times (due to freetime availability 
from calendar profile)
SchedDetailItemsFormulaLength - Length of schedule detail items formula, value 
follows CD fixed portion
COLOR_VALUE SuggBkgndColor - Suggested background color.
COLOR_VALUE SuggMouseBkgndColor - Suggested mouse background color.
COLOR_VALUE SuggSelectBkgndColor - Suggested selction background color.
DetailDisplayFormFormulaLength
wReserved[1]
dwReserved[7] - Reserved for future use. Must be zero.

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.

These fields may be followed by optional items. If you plan to use them, you 
will need to declare the variables and assign values to their lengths.

**See Also :**
[CDEMBEDDEDSCHEDCTL](/reference/Data/CDEMBEDDEDSCHEDCTL)
[EMBEDDEDSCHEDEXT_FLAG_xxx](/reference/Symb/EMBEDDEDSCHEDEXT_FLAG_xxx)
---
