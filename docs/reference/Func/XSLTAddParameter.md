##### Function : XML
##### XSLTAddParameter - Set XSLT parameter value(s)
---
```
#include <xml.h>
STATUS LNPUBLIC XSLTAddParameter(

	XSLTRANSFORMHANDLE  hXSLTransform,
	const char *szParmName,
	const char *szParmValue);
```
**Description :**

This function allows the ablitity to set parameter value(s) before calling the 
function XSLTTransform(..).   

**Parameters :**
Input :
hXSLTransform  -  allocated XSLT Transform  handle, allocated calling the function XSLTCreateTransform(..)

szParmName  -  the parameter name to set

szParmValue  -  the value of the parameter to be set

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR 

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[XSLTCreateTransform](/reference/Func/XSLTCreateTransform)
[XSLTRANSFORMHANDLE](/reference/Data/XSLTRANSFORMHANDLE)
[XSLTTransform](/reference/Func/XSLTTransform)
---
