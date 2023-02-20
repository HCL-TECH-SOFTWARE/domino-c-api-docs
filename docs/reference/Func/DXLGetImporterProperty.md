##### Function : XML
##### DXLGetImporterProperty - Get DXL importer property
---
```
#include <xml.h>
STATUS LNPUBLIC DXLGetImporterProperty(

	DXLIMPORTHANDLE  hDXLImporter,
	DXL_IMPORT_PROPERTY  prop,
	void *retPropValue);
```
**Description :**

This function retrieves the current set value of the Import Property Values 
defined in DXL_IMPORT_PROPERTY.   Call this function for each property value to 
retrieve.

**Parameters :**
Input :
hDXLImporter  -  allocated DXL Import Handle, allocated calling the function DXLCreateImporter(..)

prop  -  the Import Property Value to get

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully obtained the DXL Import Property information.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


retPropValue  -  the current set value of the Import Property



**See Also :**
[DXLIMPORTHANDLE](/reference/Data/DXLIMPORTHANDLE)
[DXLIMPORTOPTION](/reference/Data/DXLIMPORTOPTION)
[DXLSetImporterProperty](/reference/Func/DXLSetImporterProperty)
[DXL_IMPORT_PROPERTY](/reference/Data/DXL_IMPORT_PROPERTY)
---
