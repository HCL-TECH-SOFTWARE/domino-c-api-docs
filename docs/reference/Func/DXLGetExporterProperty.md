##### Function : XML
##### DXLGetExporterProperty - Get DXL exporter property
---
```
#include <xml.h>
STATUS LNPUBLIC DXLGetExporterProperty(

	DXLEXPORTHANDLE  hDXLExport,
	DXL_EXPORT_PROPERTY  prop,
	void *retPropValue);
```
**Description :**

This function retrieves the current set value of the Export Property Values 
defined in DXL_EXPORT_PROPERTY.   Call this function for each property value to 
retrieve.

**Parameters :**
Input :
hDXLExport  -  allocated DXL Export Handle, allocated calling the function DXLCreateExporter(..)

prop  -  the Export Property Value to get

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully obtained  the Export Property information.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


retPropValue  -  the current set value of the Export Property


**See Also :**
[DXLEXPORTHANDLE](/domino-c-api-docs/reference/Data/DXLEXPORTHANDLE)
[DXLSetExporterProperty](/domino-c-api-docs/reference/Func/DXLSetExporterProperty)
[DXL_EXPORT_PROPERTY](/domino-c-api-docs/reference/Data/DXL_EXPORT_PROPERTY)
---
