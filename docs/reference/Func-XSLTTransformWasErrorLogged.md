##### Function : XML
##### XSLTTransformWasErrorLogged - Test for error logged during XSLTTransform
---
##### #include <xml.h>
BOOL   LNPUBLIC **XSLTTransformWasErrorLogged(**

	XSLTRANSFORMHANDLE  hXSLTransform);
**Description :**

**Parameters :**
Input :
hXSLTransform  -  allocated XSLT Transform  handle, allocated calling the function XSLTCreateTransform(..)

Output :
(routine)  -  This returns TRUE if there was an error logged during XSLTTransform(..), FALSE otherwise. 


**See Also :**
[XSLTCreateTransform](D:/md_files/XSLTCreateTransform.md)
[XSLTRANSFORMHANDLE](D:/md_files/XSLTRANSFORMHANDLE.md)
[XSLTTransform](D:/md_files/XSLTTransform.md)
[XSLT_PROPERTY](D:/md_files/XSLT_PROPERTY.md)
---
