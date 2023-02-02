##### Data Type : Composite Data
##### CDEMBEDDEDSCHEDCTL - Specifies an embedded scheduling control.
---
##### #include <editods.h>
**Description :**
This CD record defines an embedded element of type 'group scheduler'.   It is 
preceded by a CDHOTSPOTBEGIN and a CDPLACEHOLDER.  The CD record, 
CDPLACEHOLDER, further defines the CDEMBEDDEDSCHEDCTL. 

WSIG  Header     Signature and length of this CD record
DWORD  Flags     see EMBEDDEDSCHED_FLAG_xxx
WORD  TargetFrameLength   Length of Target Frame, values follows CD fixed 
portion
WORD  DisplayStartDTItemFormulaLength Length of start date time item 
information, value follows CD fixed portion
WORD  HrsPerDayItemFormulaLength  Length of duration item information, value 
follows CD fixed portion
WORD  ReqPeopleItemsFormulaLength  Length of group member item information, 
value follows CD fixed portion
COLOR_VALUE BusyTimeColor    Color used for busy times (due to calendar entry)
COLOR_VALUE FreeTimeColor    Color used for non-busy times
COLOR_VALUE NoDataColor    Color used for no busy time data found
COLOR_VALUE DataRestrictedColor   Color used for busy time data restricted
COLOR_VALUE GridLineColor    Color used to paint grid lines in scheduler
WORD  NameColWidth    Width of the left side of the control where attendee 
names are displayed
WORD  PeopleLines    Max items in People area if 
EMBEDDEDSCHED_FLAG_PEOPLE_FIXEDHEIGHT
WORD  RoomsLines    Max items in Rooms area if 
EMBEDDEDSCHED_FLAG_ROOMS_FIXEDHEIGHT
WORD  ResourcesLines   Max items in Resources area if 
	       EMBEDDEDSCHED_RESOURCES_PEOPLE_FIXEDHEIGHT
WORD   SpareWORD[5];
DWORD  SpareDWORD[13]

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.

These fields may be followed by optional items. If you plan to use them, you 
will need to declare the variables and assign values to their lengths.
**See Also :**
[CDEMBEDDEDSCHEDCTLEXTRA](D:/md_files/CDEMBEDDEDSCHEDCTLEXTRA.md)
[CDPLACEHOLDER](D:/md_files/CDPLACEHOLDER.md)
[COLOR_VALUE](D:/md_files/COLOR_VALUE.md)
[EMBEDDEDSCHED_FLAG_xxx](D:/md_files/EMBEDDEDSCHED_FLAG_xxx.md)
---
