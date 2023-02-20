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
[XSLTCreateTransform](/reference/Func/XSLTCreateTransform)
[XSLTRANSFORMHANDLE](/reference/Data/XSLTRANSFORMHANDLE)
[XSLTTransform](/reference/Func/XSLTTransform)
[XSLT_PROPERTY](/reference/Data/XSLT_PROPERTY)
---
