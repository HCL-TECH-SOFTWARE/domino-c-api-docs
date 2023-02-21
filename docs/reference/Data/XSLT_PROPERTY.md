##### Data Type : XML
##### XSLT_PROPERTY - XSLT property
---
```
#include <xml.h>
```
**Description :**

XSLT_PROPERTY default values are set as follows:
 
 Note: (i) = can input new value into the exporter.
  (o) = can get current value out of exporter.
  (io) = can do both. 
 
 xsltResultLog   = (o) NULLMEMHANDLE
 xsltResultLogComment  = (io) NULLMEMHANDLE
 xsltExitOnFirstFatalError = (io) TRUE
 xsltInputValidationOption = (io) Xml_Validate_Auto
 xsltOutputCharset  = (io) xsltOutputUtf8

**See Also :**
[Xml_Validation_Option](/domino-c-api-docs/reference/Data/Xml_Validation_Option)
[XSLTGetTransformProperty](/domino-c-api-docs/reference/Func/XSLTGetTransformProperty)
[XSLTSetTransformProperty](/domino-c-api-docs/reference/Func/XSLTSetTransformProperty)
[XSLT_OUTPUT_CHARSET](/domino-c-api-docs/reference/Data/XSLT_OUTPUT_CHARSET)
---
