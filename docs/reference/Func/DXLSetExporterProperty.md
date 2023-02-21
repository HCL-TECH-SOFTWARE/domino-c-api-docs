##### Function : XML
##### DXLSetExporterProperty - Set DXL exporter property
---
```
#include <xml.h>
STATUS LNPUBLIC DXLSetExporterProperty(

	DXLEXPORTHANDLE  hDXLExport,
	DXL_EXPORT_PROPERTY  prop,
	void *propValue);
```
**Description :**

This function sets the Export Property Values defined in DXL_EXPORT_PROPERTY.  
Call this function for each property value to set.

**Parameters :**
Input :
hDXLExport  -  allocated DXL Export Handle, allocated calling the function DXLCreateExporter(..)

prop  -  the Export Property to set

propValue  -  value to set the Export Property, values defined in DXL_EXPORT_PROPERTY

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully set Export Property information.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**See Also :**
[DXLEXPORTHANDLE](/domino-c-api-docs/reference/Data/DXLEXPORTHANDLE)
[DXLGetExporterProperty](/domino-c-api-docs/reference/Func/DXLGetExporterProperty)
[DXL_EXPORT_PROPERTY](/domino-c-api-docs/reference/Data/DXL_EXPORT_PROPERTY)
---
