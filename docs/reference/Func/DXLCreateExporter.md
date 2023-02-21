##### Function : XML
##### DXLCreateExporter - Create DXL exporter
---
```
#include <xml.h>
STATUS LNPUBLIC DXLCreateExporter(

	DXLEXPORTHANDLE *prethDXLExport);
```
**Description :**

This function is called to initialize both the DXLEXPORTHANDLE and the 
DXL_EXPORT_PROPERTY default values.  This function  must be the first function 
called when setting up to export Domino data.


**Parameters :**
Input :
prethDXLExport  -  A DXL Export Handle needed to pass to the other DXL Import functions.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully initialized the DXLEXPORTHANDLE.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**See Also :**
[DXLDeleteExporter](/domino-c-api-docs/reference/Func/DXLDeleteExporter)
[DXLEXPORTHANDLE](/domino-c-api-docs/reference/Data/DXLEXPORTHANDLE)
[DXL_EXPORT_PROPERTY](/domino-c-api-docs/reference/Data/DXL_EXPORT_PROPERTY)
---
