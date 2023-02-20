##### Function : XML
##### DXLDeleteExporter - Delete DXL exporter
---
```
#include <xml.h>
void LNPUBLIC DXLDeleteExporter(

	DXLEXPORTHANDLE  hDXLExport);
```
**Description :**

This function unlocks and frees the DXLEXPORTHANDLE.  This function must be 
called to free up memory allocated by DXLCreateExporter.

**Parameters :**
Input :
hDXLExport  -  the allocated DXL Export Handle

Output :
(routine)  -  None.



**See Also :**
[DXLCreateExporter](/reference/Func/DXLCreateExporter)
[DXLEXPORTHANDLE](/reference/Data/DXLEXPORTHANDLE)
---
