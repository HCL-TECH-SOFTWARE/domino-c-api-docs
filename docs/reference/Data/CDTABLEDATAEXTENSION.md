##### Data Type : Composite Data
##### CDTABLEDATAEXTENSION - Specifies extended table properties.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct
	{
	WSIG Header;
	/* Fixed section ------------ */
	DWORD dwColumnSizeToFitBits1;
	DWORD dwColumnSizeToFitBits2;
	WORD  wEqualSizeTabsWidthX;
	WORD  wTabsIndentWidthX;  

	/* Each Available member can be used explicitly for data. */
	WORD  wAvailable3;
	WORD  wAvailable4;
	DWORD dwAvailable5;
	DWORD dwAvailable6;
	DWORD dwAvailable7;
	DWORD dwAvailable8;
	DWORD dwAvailable9;

	WORD  wcTabLabelFont; /* Length of Tabs Label Font */

	/* Each AvailableLength member can be used for data in the variable 
section. */
	WORD  wAvailableLength11;
	WORD  wAvailableLength12;

	WORD  wExtension2Length; /* When all Available members have been used 
up, this
	          should be used to extend to another data extension
	          for additional storage. */

	/* Variable section ------------ */
	/* The wcTabLabelFont variable data defined below is actually 
	 *   a FONTID followed by a DWORD followed by a COLOR_VALUE.
	 *   Some Notes6 pre-release versions only wrote the FONTID/DWORD 
combination 
	 *   without the trailing COLOR_VALUE, so need to verify that 
	 *   wcTabLabelFont is at least large enough to hold FONTID, DWORD, and 
COLOR_VALUE 
	 *   before trying to read off the COLOR_VALUE.  SDK consumers should
	 *   ignore the value of the DWORD when reading this structure and
	 *   write the DWORD value as 0 when writing this structure
	 */
	/* <wcTabLabelFont variable data> */
	/* <wAvailableLength11 variable data> */
	/* <wAvailableLength12 variable data> */
	/* <wExtension2Length variable data>  */
} CDTABLEDATAEXTENSION;
```

**Description :**

This record was added because the Pre Table Begin Record can not be expanded and R6 required more data to be stored.<br>
<br>
This CD record specifies extended table properties. It is preceded by CDPRETABLEBEGIN. Both records may be encapsulated within a CDBEGINRECORD and CDENDRECORD. <br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.<br>
<br>
These fields may be followed by optional items. If you plan to use them, you will need to declare the variables and assign values to their lengths.


**See Also :**
[CDPRETABLEBEGIN](/domino-c-api-docs/reference/Data/CDPRETABLEBEGIN)
---
