##### Data Type : XML
##### DXL_EXPORT_PROPERTY - DXL export property values
---
```
#include <xml.h>
```
**Description :**

DXL_EXPORT_PROPERTY default values are set as follows:
 
Note: (i) = can input new value into the exporter.
  (o) = can get current value out of exporter.
  (io) = can do both. 
 
  eDxlExportResultLog  = (o) NULLMEMHANDLE
	eDefaultDoctypeSYSTEM = (o) default filename of dtd keyed to current 
version of DXL exporter."
 eDoctypeSYSTEM  = (io) filename of dtd keyed to current version of DXL 
exporter."
  eDXLBannerComments  = (io) NULLMEMHANDLE
  eDxlExportCharset  = (io) eDxlExportUtf8
  eDxlRichtextOption  = (io) eRichtextAsDxl
	eDxlExportResultLogComment = (io) NULLMEMHANDLE
  eForceNoteFormat  = (io) FALSE
  eExitOnFirstFatalError  = (io) TRUE
  eOutputRootAttrs  = (io) TRUE
  eOutputXmlDecl  = (io) TRUE
  eOutputDOCTYPE  = (io) TRUE
	eConvertNotesbitmapToGIF = (io)  FALSE
	eDxlValidationStyle  = (io) eDxlExportValidationStyle_DTD"
 eDxlDefaultSchemaLocation = (o) URI's of schema keyed to current version of 
DLX exporter."
 eDxlSchemaLocation  = (io) filename of XML Schema keyed to current version of 
DXL exporter."


 

**See Also :**
[DXLGetExporterProperty](/reference/Func/DXLGetExporterProperty)
[DXLSetExporterProperty](/reference/Func/DXLSetExporterProperty)
[DXL_EXPORT_CHARSET](/reference/Data/DXL_EXPORT_CHARSET)
[DXL_RICHTEXT_OPTION](/reference/Data/DXL_RICHTEXT_OPTION)
---
