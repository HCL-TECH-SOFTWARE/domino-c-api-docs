##### Function : XML
##### DXLImportWasErrorLogged - Test for error logged during DXL Import
---
```
#include <xml.h>
BOOL   LNPUBLIC DXLImportWasErrorLogged(

	DXLIMPORTHANDLE  hDXLImport);
```
**Description :**



**Parameters :**
Input :
hDXLImport  -  allocated DXL import handle, allocated calling the function DXLCreateImporter(..)

Output :
(routine)  -  This returns TRUE if an error was logged during Import, FALSE otherwise. 



**See Also :**
[DXLCreateImporter](/domino-c-api-docs/reference/Func/DXLCreateImporter)
[DXLIMPORTHANDLE](/domino-c-api-docs/reference/Data/DXLIMPORTHANDLE)
---
