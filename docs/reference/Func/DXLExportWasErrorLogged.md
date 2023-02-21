##### Function : XML
##### DXLExportWasErrorLogged - Test for error logged during DXL Export
---
```
#include <xml.h>
BOOL   LNPUBLIC DXLExportWasErrorLogged(

	DXLEXPORTHANDLE  hDXLExport);
```
**Description :**



**Parameters :**
Input :
hDXLExport  -  allocated DXL Export Handle, allocated calling the function DXLCreateExporter(..)

Output :
(routine)  -  This returns TRUE if an error was logged during Export, FALSE otherwise. 



**See Also :**
[DXLCreateExporter](/domino-c-api-docs/reference/Func/DXLCreateExporter)
[DXLEXPORTHANDLE](/domino-c-api-docs/reference/Data/DXLEXPORTHANDLE)
---
