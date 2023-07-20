##### Data Type : Time
##### DTFMT - Date/Time formatting data
---
```
#include <misc.h>
```

**Definition :**
```
typedef struct {
	BYTE Preferences;   /* NPREF_xxx. Get preferences from the Client or 
from the Form/View? */
	DWORD DTFlags;   
	DWORD DTFlags2;   /* In case we need more room */
	BYTE DTDOWFmt;   /* Day-of-week format choice */
	BYTE DTYearFmt;   /* Year format choice */
	BYTE DTMonthFmt;   /* Month format choice */
	BYTE DTDayFmt;   /* Day format choice */
	BYTE DTDShow;   /* Date display choice */
	BYTE DTTShow;   /* Time display choice */
	BYTE DTDSpecial;   /* Date special display choice */
	BYTE DTTZone;   /* Time zone display choice */
	char* DTDsep1;   /* Date field separator string #1 */
	char* DTDsep2;   /* Date field separator string #2 */
	char* DTDsep3;   /* Date field separator string #3 */
	char* DTTsep;   /* Time field separator string */
} DTFMT;

```

**Description :**

This structure holds the format for date and time information.  This structure must be filled out when passed into the function IntlTIMEDATEConvertToText(..).  Please see IntlTIMEDATEConvertToText(..) for more information.


**See Also :**
[DT_DFMT_xxx](/domino-c-api-docs/reference/Symb/DT_DFMT_xxx)
[DT_DSHOW_xxx](/domino-c-api-docs/reference/Symb/DT_DSHOW_xxx)
[DT_DSPEC_xxx](/domino-c-api-docs/reference/Symb/DT_DSPEC_xxx)
[DT_GET_STYLE](/domino-c-api-docs/reference/Func/DT_GET_STYLE)
[DT_MFMT_xxx](/domino-c-api-docs/reference/Symb/DT_MFMT_xxx)
[DT_SET_STYLE](/domino-c-api-docs/reference/Func/DT_SET_STYLE)
[DT_TSHOW_xxx](/domino-c-api-docs/reference/Symb/DT_TSHOW_xxx)
[DT_WFMT_xxx](/domino-c-api-docs/reference/Symb/DT_WFMT_xxx)
[DT_xxx [CDEXT2FIELD - DTFlags2]](/domino-c-api-docs/reference/Symb/DT_xxx [CDEXT2FIELD - DTFlags2])
[DT_xxx [CDEXT2FIELD - DTFlags]](/domino-c-api-docs/reference/Symb/DT_xxx [CDEXT2FIELD - DTFlags])
[DT_YFMT_xxx](/domino-c-api-docs/reference/Symb/DT_YFMT_xxx)
[IntlTIMEDATEConvertToText](/domino-c-api-docs/reference/Func/IntlTIMEDATEConvertToText)
[NPREF_xxx](/domino-c-api-docs/reference/Symb/NPREF_xxx)
---
