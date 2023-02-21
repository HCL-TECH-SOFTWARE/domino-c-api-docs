##### Function : XML
##### XSLTCreateTransform - Create an XSLT Transform Handle.
---
```
#include <xml.h>
STATUS LNPUBLIC XSLTCreateTransform(

	XSLTRANSFORMHANDLE *prethXSLTransform);
```
**Description :**

This function is called to initialize both the XSLTRANSFORMHANDLE and the 
XSLT_PROPERTY default values.  This function  must be the first function called 
when setting up an XSLT Tranform.

**Parameters :**
Input :
prethXSLTransform  -  An XSLT Transform Handle which is needed to pass to the other XSLT functions. 

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR 

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[XSLTRANSFORMHANDLE](/domino-c-api-docs/reference/Data/XSLTRANSFORMHANDLE)
[XSLTTransformDeleteTransform](/domino-c-api-docs/reference/Func/XSLTTransformDeleteTransform)
[XSLT_PROPERTY](/domino-c-api-docs/reference/Data/XSLT_PROPERTY)
---
