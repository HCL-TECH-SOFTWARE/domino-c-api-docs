##### Function : XML
##### DXLDeleteImporter - Delete DXL importer
---
```
#include <xml.h>
void LNPUBLIC DXLDeleteImporter(

	DXLIMPORTHANDLE  hDXLImport);
```
**Description :**

This function unlocks and frees the DXLIMPORTHANDLE.  This function must be 
called to free up memory allocated by DXLCreateImporter.


**Parameters :**
Input :
hDXLImport  -  allocated DXL Import Handle

Output :
(routine)  -  None.



**See Also :**
[DXLCreateImporter](/domino-c-api-docs/reference/Func/DXLCreateImporter)
[DXLIMPORTHANDLE](/domino-c-api-docs/reference/Data/DXLIMPORTHANDLE)
---
