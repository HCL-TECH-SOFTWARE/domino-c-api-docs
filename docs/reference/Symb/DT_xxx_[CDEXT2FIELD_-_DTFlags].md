##### Symbolic Value : Constants
##### DT_xxx [CDEXT2FIELD - DTFlags] - CDEXT2FIELD - DTFlags
---
```
#include <misc.h>
```

**Symbolic Values :**

	DT_VALID	  -  Validity bit: If 1, use new DTFMT; if 0, use old TFMT

	DT_4DIGITYEAR	  -  Require 4 digit year on INPUT (not output)

	DT_ALPHAMONTH	  -  Require months be INPUT as letters, not digits (e.g. "jan", not 01)

	DT_SHOWTIME	  -  Display time element on output

	DT_SHOWDATE	  -  Display date element on output

	DT_24HOUR	  -  Display time on output using 24 hour clock format

	DT_STYLE_YMD	  -  Date element order: Year, Month, Day, Day-of-week

	DT_STYLE_MDY	  -  Date element order: Day-of-week, Month, Day, Year

	DT_STYLE_DMY	  -  Date element order: Day-of-week, Day, Month, Year

	DT_STYLE_MSK	  -  This is where we store the style value in DTFlags


**Description :**




**See Also :**
[CDEXT2FIELD](/domino-c-api-docs/reference/Data/CDEXT2FIELD)
[DT_GET_STYLE](/domino-c-api-docs/reference/Func/DT_GET_STYLE)
[DT_SET_STYLE](/domino-c-api-docs/reference/Func/DT_SET_STYLE)
---
