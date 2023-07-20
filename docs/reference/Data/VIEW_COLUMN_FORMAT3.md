##### Data Type : Views
##### VIEW_COLUMN_FORMAT3 - Extended View column format descriptor.
---
```
#include <viewfmt.h>
```

**Definition :**
```
typedef struct
{
   WORD  Signature;      /* VIEW_COLUMN_FORMAT_SIGNATURE3 */
                         /* Date/time formatting data */
   BYTE  DTPref;         /* NPREF_xxx */
   DWORD DTFlags;        /* DT_xxx */
   DWORD DTFlags2;       /* DT_xxx */
   BYTE  DTDOWFmt;       /* DT_WFMT_xxx */
   BYTE  DTYearFmt;      /* DT_YFMT_xxx */
   BYTE  DTMonthFmt;     /* DT_MFMT_xxx */
   BYTE  DTDayFmt;       /* DT_DFMT_xxx */
   BYTE  DTDsep1Len;
   BYTE  DTDsep2Len;
   BYTE  DTDsep3Len;
   BYTE  DTTsepLen;
   BYTE  DTDShow;        /* DT_DSHOW_xxx */
   BYTE  DTDSpecial;     /* DT_DSPEC_xxx */
   BYTE  DTTShow;        /* DT_TSHOW_xxx */
   BYTE  DTTZone;        /* TZFMT_xxx */
   WORD  DatePreference;
   BYTE  bUnused;
   DWORD Unused;
} VIEW_COLUMN_FORMAT3;
```

**Description :**




**See Also :**
[VIEW_COLUMN_FORMAT](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT)
[VIEW_TABLE_FORMAT](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT)
[VIEW_TABLE_FORMAT2](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT2)
---
