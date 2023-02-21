##### Function : XML
##### DXLSetImporterProperty - Set DXL importer property
---
```
#include <xml.h>
STATUS LNPUBLIC DXLSetImporterProperty(

	DXLIMPORTHANDLE  hDXLImport,
	DXL_IMPORT_PROPERTY  prop,
	void *propValue);
```
**Description :**

This function sets the Import Property Values defined in DXL_IMPORT_PROPERTY.  
Call this function for each property value to set.


**Parameters :**
Input :
hDXLImport  -  allocated DXL Import Handle, allocated calling the function DXLCreateImporter(..)


prop  -  the Import Property to set

propValue  -  value to set the Import Property, values defined in DXL_IMPORT_PROPERTY

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully set the import property value..

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**See Also :**
[DXLGetImporterProperty](/domino-c-api-docs/reference/Func/DXLGetImporterProperty)
[DXLIMPORTHANDLE](/domino-c-api-docs/reference/Data/DXLIMPORTHANDLE)
[DXLIMPORTOPTION](/domino-c-api-docs/reference/Data/DXLIMPORTOPTION)
[DXL_IMPORT_PROPERTY](/domino-c-api-docs/reference/Data/DXL_IMPORT_PROPERTY)
---
