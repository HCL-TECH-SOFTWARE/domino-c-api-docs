##### Function : XML
##### XSLTTransformWasErrorLogged - Test for error logged during XSLTTransform
---
```
#include <xml.h>
BOOL   LNPUBLIC XSLTTransformWasErrorLogged(

	XSLTRANSFORMHANDLE  hXSLTransform);
```
**Description :**



**Parameters :**
Input :
hXSLTransform  -  allocated XSLT Transform  handle, allocated calling the function XSLTCreateTransform(..)

Output :
(routine)  -  This returns TRUE if there was an error logged during XSLTTransform(..), FALSE otherwise. 



**See Also :**
[XSLTCreateTransform](/domino-c-api-docs/reference/Func/XSLTCreateTransform)
[XSLTRANSFORMHANDLE](/domino-c-api-docs/reference/Data/XSLTRANSFORMHANDLE)
[XSLTTransform](/domino-c-api-docs/reference/Func/XSLTTransform)
[XSLT_PROPERTY](/domino-c-api-docs/reference/Data/XSLT_PROPERTY)
---
