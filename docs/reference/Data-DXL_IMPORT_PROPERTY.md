##### Data Type : XML
##### DXL_IMPORT_PROPERTY - DXL import property values
---
##### #include <xml.h>
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
[DXLGetImporterProperty](D:/md_files/DXLGetImporterProperty.md)
[DXLIMPORTOPTION](D:/md_files/DXLIMPORTOPTION.md)
[DXLLOGOPTION](D:/md_files/DXLLOGOPTION.md)
[DXLSetImporterProperty](D:/md_files/DXLSetImporterProperty.md)
[Xml_Validation_Option](D:/md_files/Xml_Validation_Option.md)
---
