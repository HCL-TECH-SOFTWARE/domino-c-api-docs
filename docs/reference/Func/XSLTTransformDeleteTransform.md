##### Function : XML
##### XSLTTransformDeleteTransform - Delete this XSLT Tranform
---
```
#include <xml.h>
void   LNPUBLIC XSLTTransformDeleteTransform(

	XSLTRANSFORMHANDLE  hXSLTransform);
```
**Description :**

This function unlocks and frees the XSLTRANSFORMHANDLE.  This function must be 
called to free up memory allocated by XSLTCreateTransform.

**Parameters :**
Input :
hXSLTransform  -  the allocated XSLT Tranform Handle

Output :
(routine)  -  None



**See Also :**
[XSLTCreateTransform](/domino-c-api-docs/reference/Func/XSLTCreateTransform)
[XSLTRANSFORMHANDLE](/domino-c-api-docs/reference/Data/XSLTRANSFORMHANDLE)
---
