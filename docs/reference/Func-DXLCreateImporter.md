##### Function : XML
##### DXLCreateImporter - Create DXL importer
---
##### #include <xml.h>
STATUS LNPUBLIC **DXLCreateImporter(**

	DXLIMPORTHANDLE *prethDXLImport);
**Description :**
This function initializes both the DXLIMPORTHANDLE and the DXL_IMPORT_PROPERTY 
default values.  This function must be the first function called prior to 
importing Domino XML data.  

**Parameters :**
Input :
prethDXLImport  -  A DXL Import Handle needed to pass to the other DXL Import functions.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully allocated the DXLIMPORTHANDLE.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


**See Also :**
[DXLDeleteImporter](D:/md_files/DXLDeleteImporter.md)
[DXLIMPORTHANDLE](D:/md_files/DXLIMPORTHANDLE.md)
[DXL_IMPORT_PROPERTY](D:/md_files/DXL_IMPORT_PROPERTY.md)
---
