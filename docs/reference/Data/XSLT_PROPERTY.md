##### Data Type : XML
##### XSLT_PROPERTY - XSLT property
---
```
#include <xml.h>
```

**Definition :**

typedef enum
{
	xsltResultLog=1,   /* MEMHANDLE,   Readonly - the result log from the 
last transform. */
	xsltResultLogComment=2,  /* char*(i)/MEMHANDLE(o),  LMBCS string to be 
added as comment to top of result log */
	xsltExitOnFirstFatalError=3, /* BOOL,  TRUE = importer exits on first 
fatal error, */
	     /*   FALSE = importer continues even if fatal error found */
	xsltInputValidationOption=4, /* Xml_Validation_Option,Values defined in 
Xml_Validation_Option: 
	        ...Validate_Never, ...Validate_Always, ...Validate_Auto */
	xsltOutputCharset=5   /* XSLT_OUTPUT_CHARSET,xsltOutputUtf8 or 
xsltOutputUtf16 */

} XSLT_PROPERTY;

**Description :**

XSLT_PROPERTY default values are set as follows:<br>
 <br>
 Note:	(i) = can input new value into the exporter.<br>
 	(o) = can get current value out of exporter.<br>
 	(io) = can do both. <br>
 <br>
 xsltResultLog			= (o)	NULLMEMHANDLE<br>
 xsltResultLogComment		= (io)	NULLMEMHANDLE<br>
 xsltExitOnFirstFatalError	= (io)	TRUE<br>
 xsltInputValidationOption	= (io)	Xml_Validate_Auto<br>
 xsltOutputCharset		= (io)	xsltOutputUtf8


**See Also :**
[Xml_Validation_Option](/domino-c-api-docs/reference/Data/Xml_Validation_Option)
[XSLTGetTransformProperty](/domino-c-api-docs/reference/Func/XSLTGetTransformProperty)
[XSLTSetTransformProperty](/domino-c-api-docs/reference/Func/XSLTSetTransformProperty)
[XSLT_OUTPUT_CHARSET](/domino-c-api-docs/reference/Data/XSLT_OUTPUT_CHARSET)
---
