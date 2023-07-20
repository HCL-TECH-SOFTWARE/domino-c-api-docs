##### Symbolic Value : Constants
##### VCF_HIDE_xxx - VIEW_COLUMN_FORMAT2 - wCustomHiddenFlags.
---
```
#include <viewfmt.h>
```

**Symbolic Values :**

	VCF_HIDE_S_NormalView	  -  (Shift) Hide column if in normal view

	VCF_HIDE_M_NormalView	  -  (Mask) Hide column if in normal view

	VCF_HIDE_S_CalFormatTwoDay	  -  (Shift) Hide column if in two day calendar view

	VCF_HIDE_M_CalFormatTwoDay	  -  (Mask) Hide column if in two day calendar view

	VCF_HIDE_S_CalFormatOneWeek	  -  (Shift) Hide column if in one week calendar view

	VCF_HIDE_M_CalFormatOneWeek	  -  (Mask) Hide column if in one week calendar view

	VCF_HIDE_S_CalFormatTwoWeeks	  -  (Shift) Hide column if in two week calendar view

	VCF_HIDE_M_CalFormatTwoWeeks	  -  (Mask) Hide column if in two week calendar view

	VCF_HIDE_S_CalFormatOneMonth	  -  (Shift) Hide column if in one month calendar view

	VCF_HIDE_M_CalFormatOneMonth	  -  (Mask) Hide column if in one month calendar view

	VCF_HIDE_S_CalFormatOneYear	  -  (Shift) Hide column if in one year calendar view

	VCF_HIDE_M_CalFormatOneYear	  -  (Mask) Hide column if in one year calendar view

	VCF_HIDE_S_CalFormatOneDay	  -  (Shift) Hide column if in one day calendar view

	VCF_HIDE_M_CalFormatOneDay	  -  (Mask) Hide column if in one day calendar view

	VCF_HIDE_S_CalFormatWorkWeek	  -  (Shift) Hide column if in work week calendar view

	VCF_HIDE_M_CalFormatWorkWeek	  -  (Mask) Hide column if in work week calendar view

	VCF_HIDE_S_DB2_MAPPING	  -  (Shift) Column mapped to DB2 data type.

	VCF_HIDE_M_DB2_MAPPING	  -  (Mask) Column mapped to DB2 data type.

	VCF_HIDE_S_DB2_DATATYPE_TEXT	  -  (Shift) Column mapped to DB2 data type TEXT.

	VCF_HIDE_M_DB2_DATATYPE_TEXT	  -  (Mask) Column mapped to DB2 data type TEXT.

	VCF_HIDE_S_DB2_DATATYPE_NUMBER	  -  (Shift) Column mapped to DB2 data type NUMBER.

	VCF_HIDE_M_DB2_DATATYPE_NUMBER	  -  (Mask) Column mapped to DB2 data type NUMBER.

	VCF_HIDE_S_DB2_DATATYPE_TIMEDATE	  -  (Shift) Column mapped to DB2 data type TIMEDATE.

	VCF_HIDE_M_DB2_DATATYPE_TIMEDATE	  -  (Mask) Column mapped to DB2 data type TIMEDATE.

	VCF_HIDE_S_DB2_DATATYPE_NONE	  -  (Shift) Select Column mapping to DB2 data type.

	VCF_HIDE_M_DB2_DATATYPE_NONE	  -  (Mask) Select Column mapping to DB2 data type.


**Description :**

Values for wCustomHiddenFlags member of VIEW_COLUMN_FORMAT2. In the calendar view, hidden columns may be saved on a per calendar format basis. If the calendar format's day display area is small (ex: a one month calendar format), you may wish to hide more columns than when the day display is larger (ex: a two day calendar format).


**See Also :**
[VIEW_COLUMN_FORMAT2](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT2)
---
