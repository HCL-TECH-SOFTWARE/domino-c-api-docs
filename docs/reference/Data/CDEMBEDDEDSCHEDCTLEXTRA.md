##### Data Type : Composite Data
##### CDEMBEDDEDSCHEDCTLEXTRA - Extended field attributes for CDEMBEDDEDSCHEDCTL.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct
	{
	WSIG  Header;
	WORD  FixedPartLength;  /* bytes of this structure */
	DWORD  Flags;     /* EMBEDDEDSCHEDEXT_FLAG_xxx from above */

	/* Colors used for the scheduler ODLists */

	COLOR_VALUE SchedHdrBkgndColor;  /* Bkgnd color for the Scheduler 
ODList headers */
	COLOR_VALUE SchedHdrFontColor;  /* Font color for the Scheduler ODList 
headers */

	COLOR_VALUE SchedBkgndColor;     /* Bkgnd color for the scheduler 
ODList */

	COLOR_VALUE NameHdrBkgndColor;  /* Bkgnd color for name ODList header 
area*/
	COLOR_VALUE NameHdrFontColor;  /* Font color for name ODList header 
area */

	COLOR_VALUE NameBkgndColor;  /* Normal bkgnd color for attendee names */
	COLOR_VALUE NameMouseBkgndColor; /* Mouse over bkgnd color for attendee 
names */
	COLOR_VALUE NameSelectBkgndColor; /* Select bkgnd color for attendee 
names */

	COLOR_VALUE NameFontColor;   /* Normal font color for attendee names */
	COLOR_VALUE NameMouseFontColor;  /* Mouse over font color for attendee 
names */
	COLOR_VALUE NameSelectFontColor; /* Select font color for attendee 
names */

	/* Formula & text lengths */
	WORD  OptPeopleItemsFormulaLength;
	WORD  ReqRoomsItemsFormulaLength;
	WORD  OptRoomsItemsFormulaLength;
	WORD  ReqResourcesItemsFormulaLength;
	WORD  OptResourcesItemsFormulaLength;
	WORD  IntervalStartDTItemFormulaLength;
	WORD  IntervalEndDTItemFormulaLength;
	WORD  SchedulerNameLength;
	WORD  PeopleTitleLength;
	WORD  RoomsTitleLength;
	WORD  ResourcesTitleLength;
	WORD  IntervalChangeEventFormulaLength;
	COLOR_VALUE ProfileColor; /* Color used to paint busy times (due to 
freetime availability from calendar profile) */
	WORD  SchedDetailItemsFormulaLength;

	COLOR_VALUE SuggBkgndColor;   /* bkgnd colors for suggestions odlist */
	COLOR_VALUE SuggMouseBkgndColor;
	COLOR_VALUE SuggSelectBkgndColor;

	WORD  DetailDisplayFormFormulaLength;
	WORD  SuggestionsAvailEventFormulaLength;
	WORD  wReserved[2];

	DWORD  dwReserved[6];   /* Reserved for future use, must be zero */

	/* Variable length data follows if specified */
	/* OptionalPeopleItems formula (if any) */
	/* RequiredRoomsItems formula (if any) */
	/* OptionalRoomsItems formula (if any) */
	/* RequiredResourcesItems formula (if any) */
	/* OptionalResourcesItems formula (if any) */
	/* IntervalStartDT formula (if any) */
	/* IntervalEndDT formula (if any) */
	/* SchedulerName (if any) */
	/* People Title (if any) */
	/* Rooms Title (if any) */
	/* Resources Title (if any) */
	/* Appointment Interval Change Event Formula (if any) */
	/* SchedDetailItemsFormula (if any) */
	/* DetailDisplayFormFormula (if any) */
	/* SuggestionsAvailEventFormula (if any) */
	} CDEMBEDDEDSCHEDCTLEXTRA;

```

**Description :**

<br>
New field attributes have been added in Notes/Domino 6.  To preserve compatibility with existing applications, the new attributes have been placed in this extension to the CDEMBEDDEDSCHEDCTL record.  This record is optional, and may not be present in the $Body item of the form note.<br>
<br>
The fields in this structure are:<br>
<br>
Header - Signature and length of this CD record<br>
FixedPartLength - Length in bytes of this structure<br>
Flags - See EMBEDDEDSCHEDEXT_FLAG_xxx<br>
SchedHdrBkgndColor - Background color of scheduler headers<br>
SchedHdrFontColor - Font color of scheduler headers<br>
SchedBkgndColor - Background color of scheduler <br>
NameHdrBkgndColor - Background color of name header area <br>
NameHdrFontColor - Font color of name header area<br>
NameBkgndColor - Normal background color of attendee names<br>
NameMouseBkgndColor - Mouse over background color of attendee names<br>
NameSelectBkgndColor - Select background color of attendee names<br>
NameFontColor - Normal font color of attendee names<br>
NameMouseFontColor - Mouse over font color of attendee names<br>
NameSelectFontColor - Select font color of attendee names<br>
OptPeopleItemsFormulaLength - Length of optional people items formula, value follows CD fixed portion<br>
ReqRoomsItemsFormulaLength - Length of required rooms items formula, value follows CD fixed portion<br>
OptRoomsItemsFormulaLength - Length of optional rooms items formula, value follows CD fixed portion<br>
ReqResourcesItemsFormulaLength - Length of required resources items formula, value follows CD fixed portion<br>
OptResourcesItemsFormulaLength - Length of optional resources items formula, value follows CD fixed portion<br>
IntervalStartDTItemFormulaLength - Length of interval start date time item formula, value follows CD fixed portion<br>
IntervalEndDTItemFormulaLength - Length of interval end date time item formula, value follows CD fixed portion<br>
SchedulerNameLength - Length of scheduler name, value follows CD fixed portion<br>
PeopleTitleLength - Length of people title, values follows CD fixed portion<br>
RoomsTitleLength - Length of rooms title, values follows CD fixed portion<br>
ResourcesTitleLength - Length of resources title, value follows CD fixed portion<br>
IntervalChangeEventFormulaLength - Length of interval change event formula, value follows CD fixed portion<br>
ProfileColor - Color used to paint busy times (due to freetime availability from calendar profile)<br>
SchedDetailItemsFormulaLength - Length of schedule detail items formula, value follows CD fixed portion<br>
COLOR_VALUE	SuggBkgndColor - Suggested background color.<br>
COLOR_VALUE SuggMouseBkgndColor - Suggested mouse background color.<br>
COLOR_VALUE SuggSelectBkgndColor - Suggested selction background color.<br>
DetailDisplayFormFormulaLength<br>
wReserved[1]<br>
dwReserved[7] - Reserved for future use. Must be zero.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.<br>
<br>
These fields may be followed by optional items. If you plan to use them, you will need to declare the variables and assign values to their lengths.


**See Also :**
[CDEMBEDDEDSCHEDCTL](/domino-c-api-docs/reference/Data/CDEMBEDDEDSCHEDCTL)
[EMBEDDEDSCHEDEXT_FLAG_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDSCHEDEXT_FLAG_xxx)
---
