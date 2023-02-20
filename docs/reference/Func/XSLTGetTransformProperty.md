##### Function : XML
##### XSLTGetTransformProperty - Get an XSLT Tranform Property Value
---
```
#include <xml.h>
STATUS LNPUBLIC XSLTGetTransformProperty(

	XSLTRANSFORMHANDLE  hXSLTransform,
	XSLT_PROPERTY  prop,
	void *retPropValue);
```
**Description :**

This function retrieves the current set value of the XSLT Property Values 
defined in XSLT_PROPERTY.   Call this function for each property value to 
retrieve.

**Parameters :**
Input :
hXSLTransform  -  allocated XSLT Tranform Handle, allocated calling the function XSLTCreateTransform(..)

prop  -  the XSLT property value to get

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR 

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retPropValue  -  the current set value of this XSLT Property member


**See Also :**
[XSLTCreateTransform](/reference/Func/XSLTCreateTransform)
[XSLTRANSFORMHANDLE](/reference/Data/XSLTRANSFORMHANDLE)
[XSLT_PROPERTY](/reference/Data/XSLT_PROPERTY)
---
