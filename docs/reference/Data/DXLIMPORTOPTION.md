##### Data Type : XML
##### DXLIMPORTOPTION - DXL importer options for ACL, design elements, and documents
---
```
#include <xml.h>
```

**Definition :**
```
typedef enum
{
	DXLIMPORTOPTION_IGNORE=1,   /* ignore imported data */
	DXLIMPORTOPTION_CREATE=2,   /* create new data from imported data */
	DXLIMPORTOPTION_IGNORE_ELSE_CREATE=3, /* if imported data matches 
existing data, ignore the imported data, */
	      /* ... otherwise create it */
	DXLIMPORTOPTION_CREATE_RESERVED2=4, /* do not used - reserved for 
future variation of create option */

	DXLIMPORTOPTION_REPLACE_ELSE_IGNORE=5, /* if imported data matches 
existing data, then replace existing */
	      /* ... data with imported data, else ignore imported data. */
	DXLIMPORTOPTION_REPLACE_ELSE_CREATE=6, /* if imported data matches 
existing data, then replace existing */
	      /* ... data with imported data, else create new data from 
imported data */
	DXLIMPORTOPTION_REPLACE_RESERVED1=7, /* do not used - reserved for 
future variation of replace option */
	DXLIMPORTOPTION_REPLACE_RESERVED2=8, /* do not used - reserved for 
future variation of replace option */

	DXLIMPORTOPTION_UPDATE_ELSE_IGNORE=9, /* if imported  data matches 
existing data, then update existing */
	      /* ... data with imported data, else ignore imported data. */
	DXLIMPORTOPTION_UPDATE_ELSE_CREATE=10, /* if imported data matches 
existing data, then update existing */
	      /* ... data with imported data, else create new data from 
	          imported data */
	DXLIMPORTOPTION_UPDATE_RESERVED1=11, /* do not used - reserved for 
future variation of update option */
	DXLIMPORTOPTION_UPDATE_RESERVED2=12 /* do not used - reserved for 
future variation of update option */

} DXLIMPORTOPTION;
```

**Description :**




**See Also :**
[DXLGetImporterProperty](/domino-c-api-docs/reference/Func/DXLGetImporterProperty)
[DXLSetImporterProperty](/domino-c-api-docs/reference/Func/DXLSetImporterProperty)
[DXL_IMPORT_PROPERTY](/domino-c-api-docs/reference/Data/DXL_IMPORT_PROPERTY)
---
