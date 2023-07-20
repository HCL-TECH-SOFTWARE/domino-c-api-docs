##### Data Type : Views
##### VIEW_COLUMN_FORMAT4 - Extended View column format descriptor.
---
```
#include <viewfmt.h>
```

**Definition :**
```
typedef struct
{
   WORD  Signature;          /* VIEW_COLUMN_FORMAT_SIGNATURE4 */
                             /* Numeric symbol data */
   NFMT  NumberFormat;
   BYTE  NumSymPref;         /* NPREF_xxx */
   BYTE  NumSymFlags;        /* NNUMSYM_xxx */
   DWORD DecimalSymLength;
   DWORD MilliSepSymLength;
   DWORD NegativeSymLength;
   WORD  MilliGroupSize;
   DWORD Unused1;
   DWORD Unused2;
                             /* Currency data */
   BYTE  CurrencyPref;       /* NPREF_xxx */
   BYTE  CurrencyType;       /* NCURFMT_xxx */
   BYTE  CurrencyFlags;      /* NCURFMT_xxx */
   DWORD CurrencySymLength;
   DWORD ISOCountry;
   WORD  NumberPreference; 
   BYTE  bUnused;
   DWORD Unused3;
   DWORD Unused4;
} VIEW_COLUMN_FORMAT4;
```

**Description :**




**See Also :**
[VIEW_COLUMN_FORMAT](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT)
[VIEW_TABLE_FORMAT](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT)
[VIEW_TABLE_FORMAT2](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT2)
---
