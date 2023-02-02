##### Function : XML
##### DXLGetImporterProperty - Get DXL importer property
---
##### #include <xml.h>
STATUS LNPUBLIC **DXLGetImporterProperty(**

	DXLIMPORTHANDLE  hDXLImporter,
	DXL_IMPORT_PROPERTY  prop,
	void *retPropValue);
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
[DXLIMPORTHANDLE](D:/md_files/DXLIMPORTHANDLE.md)
[DXLIMPORTOPTION](D:/md_files/DXLIMPORTOPTION.md)
[DXLSetImporterProperty](D:/md_files/DXLSetImporterProperty.md)
[DXL_IMPORT_PROPERTY](D:/md_files/DXL_IMPORT_PROPERTY.md)
---
