##### Data Type : XML
##### Xml_Validation_Option - Values for XML validation options.
---
```
#include <xml.h>
```

**Definition :**
```
typedef enum
{
	Xml_Validate_Never = 0,
	Xml_Validate_Always = 1,
	Xml_Validate_Auto = 2

} Xml_Validation_Option;
```

**Description :**

These values can be used to set members within the DXL_IMPORT_PROPERTY structure and the XSLT_PROPERTY structure.  For the DXL_IMPORT_PROPERTY structure the member is iInputValidationOption and for the XSLT_PROPERTY structure the member is xsltInputValidationOption.


**See Also :**
[DXL_IMPORT_PROPERTY](/domino-c-api-docs/reference/Data/DXL_IMPORT_PROPERTY)
[XSLT_PROPERTY](/domino-c-api-docs/reference/Data/XSLT_PROPERTY)
---
