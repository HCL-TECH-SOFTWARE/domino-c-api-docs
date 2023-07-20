##### Data Type : Composite Data
##### CDEMBEDDEDSCHEDCTL - Specifies an embedded scheduling control.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
 WSIG   Header;  /* Signature and length of this record. */
 DWORD  Flags;  /* EMBEDDEDSCHED_FLAG_xxx from above */
 WORD   TargetFrameLength;
 WORD  DisplayStartDTItemFormulaLength;
 WORD   HrsPerDayItemFormulaLength;
 WORD  ReqPeopleItemsFormulaLength;
 COLOR_VALUE BusyTimeColor; /* Color used for busy times (due to calendar 
entry) */
 COLOR_VALUE FreeTimeColor; /* Color used for non-busy times */
 COLOR_VALUE NoDataColor; /* Color used for no busy time data found */
 COLOR_VALUE DataRestrictedColor; /* Color used for busy time data restricted */
 COLOR_VALUE GridLineColor; /* Color used to paint grid lines in scheduler */
	WORD  NameColWidth; /* width of the left side of the control where 
attendee names are displayed */
 WORD  PeopleLines; /* Max items in People area if 
EMBEDDEDSCHED_FLAG_PEOPLE_FIXEDHEIGHT */
 WORD  RoomsLines;  /* Max items in Rooms area if 
EMBEDDEDSCHED_FLAG_ROOMS_FIXEDHEIGHT */
 WORD  ResourcesLines; /* Max items in Resources area if 
EMBEDDEDSCHED_RESOURCES_PEOPLE_FIXEDHEIGHT */
	WORD   SpareWORD[5];
 DWORD  SpareDWORD[13];

	/* Target Frame Name (if any) */
 /* DisplayStartDTItem formula (if any) */
 /* HrsPerDayItem formula (if any) */
 /* RequiredPeopleItems formula (if any) */
} CDEMBEDDEDSCHEDCTL;
```

**Description :**

This CD record defines an embedded element of type 'group scheduler'.   It is preceded by a CDHOTSPOTBEGIN and a CDPLACEHOLDER.  The CD record, CDPLACEHOLDER, further defines the CDEMBEDDEDSCHEDCTL. <br>

<ul>WSIG		Header					Signature and length of this CD record<br>
DWORD		Flags					see EMBEDDEDSCHED_FLAG_xxx<br>
WORD		TargetFrameLength			Length of Target Frame, values follows CD fixed portion<br>
WORD		DisplayStartDTItemFormulaLength	Length of start date time item information, value follows CD fixed portion<br>
WORD		HrsPerDayItemFormulaLength		Length of duration item information, value follows CD fixed portion<br>
WORD		ReqPeopleItemsFormulaLength		Length of group member item information, value follows CD fixed portion<br>
COLOR_VALUE	BusyTimeColor				Color used for busy times (due to calendar entry)<br>
COLOR_VALUE	FreeTimeColor				Color used for non-busy times<br>
COLOR_VALUE	NoDataColor				Color used for no busy time data found<br>
COLOR_VALUE	DataRestrictedColor			Color used for busy time data restricted<br>
COLOR_VALUE	GridLineColor				Color used to paint grid lines in scheduler<br>
WORD		NameColWidth				Width of the left side of the control where attendee names are displayed<br>
WORD		PeopleLines				Max items in People area if EMBEDDEDSCHED_FLAG_PEOPLE_FIXEDHEIGHT<br>
WORD		RoomsLines				Max items in Rooms area if EMBEDDEDSCHED_FLAG_ROOMS_FIXEDHEIGHT<br>
WORD		ResourcesLines			Max items in Resources area if <br>
								EMBEDDEDSCHED_RESOURCES_PEOPLE_FIXEDHEIGHT<br>
WORD 		SpareWORD[5];<br>
DWORD		SpareDWORD[13]<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.<br>
<br>
These fields may be followed by optional items. If you plan to use them, you will need to declare the variables and assign values to their lengths.</ul>



**See Also :**
[CDEMBEDDEDSCHEDCTLEXTRA](/domino-c-api-docs/reference/Data/CDEMBEDDEDSCHEDCTLEXTRA)
[CDPLACEHOLDER](/domino-c-api-docs/reference/Data/CDPLACEHOLDER)
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[EMBEDDEDSCHED_FLAG_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDSCHED_FLAG_xxx)
---
