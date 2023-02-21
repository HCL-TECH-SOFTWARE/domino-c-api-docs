##### Function : XML
##### XSLTSetTransformProperty - Set an XSLT Transform Property Value
---
```
#include <xml.h>
STATUS LNPUBLIC XSLTSetTransformProperty(

	XSLTRANSFORMHANDLE  hXSLTransform,
	XSLT_PROPERTY  prop,
	void *propValue);
```
**Description :**

This function sets the XSLT Property Values defined in XSLT_PROPERTY.  Call 
this function for each property value to set.

**Parameters :**
Input :
hXSLTransform  -  allocated XSLT Tranform Handle, allocated calling the function XSLTCreateTransform(..)

prop  -   XSLT Property member to set, defined in XSLT_PROPERTY

propValue  -  value to set this XSLT Property member to

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR 

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[XSLTCreateTransform](/domino-c-api-docs/reference/Func/XSLTCreateTransform)
[XSLTRANSFORMHANDLE](/domino-c-api-docs/reference/Data/XSLTRANSFORMHANDLE)
[XSLT_PROPERTY](/domino-c-api-docs/reference/Data/XSLT_PROPERTY)
---
