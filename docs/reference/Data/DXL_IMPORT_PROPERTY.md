##### Data Type : XML
##### DXL_IMPORT_PROPERTY - DXL import property values
---
```
#include <xml.h>
```
**Description :**

DXL_IMPORT_PROPERTY default values are set as follows:
 
 Note: (i) = can input new value into the importer.
  (o) = can get current value out of importer.
  (io) = can do both. 
 
  iACLImportOption   = (io) DXLIMPORTOPTION_IGNORE
  iDesignImportOption   = (io) DXLIMPORTOPTION_IGNORE
  iDocumentsImportOption  = (io) DXLIMPOROPTION_CREATE
  iCreateFullTextIndex   = (io) FALSE

	 note: To create a Full Text Index on a database, the 
iCreateFullTextIndex must be set to TRUE,
	            the iReplaceDbProperties must be set to TRUE and a schema 
element named <fulltextsettings>
	           must be defined.

  iReplaceDbProperties   = (io) FALSE
  iInputValidationOption   = (io) Xml_Validate_Auto
  iReplicaRequiredForReplaceOrUpdate = (io) TRUE
  iExitOnFirstFatalError   = (io) TRUE
  iUnknownTokenLogOption  = (io) DXLLOGOPTION_FATALERROR
  iResultLogComment   = (io) NULLMEMHANDLE
  iResultLog    = (o)  NULLMEMHANDLE
	iImportedNoteList   = (o)  NULLHANDLE


**See Also :**
[DXLGetImporterProperty](/reference/Func/DXLGetImporterProperty)
[DXLIMPORTOPTION](/reference/Data/DXLIMPORTOPTION)
[DXLLOGOPTION](/reference/Data/DXLLOGOPTION)
[DXLSetImporterProperty](/reference/Func/DXLSetImporterProperty)
[Xml_Validation_Option](/reference/Data/Xml_Validation_Option)
---
