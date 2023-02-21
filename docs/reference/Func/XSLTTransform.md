##### Function : XML
##### XSLTTransform - Transform XML data
---
```
#include <xml.h>
STATUS LNPUBLIC XSLTTransform(

	XSLTRANSFORMHANDLE  hXSLTransform,
	XML_READ_FUNCTION  pXSL_XMLInputFunc,
	void far *pXSL_XMLInputAction,
	XML_READ_FUNCTION  pXSL_StylesheetInputFunc,
	void far *pXSL_StylesheetInputAction,
	XML_WRITE_FUNCTION  pXSL_TransformOutputFunc,
	void far *pXSL_TransformOutputAction);
```
**Description :**

This function transforms the XML data as input into the desired format on 
output based on the stylesheet provided.

**Parameters :**
Input :
hXSLTransform  -  allocated XSLT Transform  handle, allocated calling the function XSLTCreateTransform(..)


pXSL_XMLInputFunc  -  this is a user defined read function (XML_READ_FUNCTION) supplying the XML data to be transformed

pXSL_XMLInputAction  -  a pointer to user defined data (optional) which will get passed along to the XML_READ_FUNCTION (pXSL_XMLInputFunc)

pXSL_StylesheetInputFunc  -  this is a user defined read function (XML_READ_FUNCTION( supplying the Stylesheet to be used in the transformation

pXSL_StylesheetInputAction  -   pointer to user defined data (optional) which will get passed along to the XML_READ_FUNCTION (pXSL_StylesheetInputAction)

pXSL_TransformOutputFunc  -  this is a user defined write (XML_WRITE_FUNCTION) function which will be called with the XML data that has been transformed 

pXSL_TransformOutputAction  -  pointer to user defined data (optional) which will get passed along to the XML_WRITE_FUNCTION (pXSL_TransformOutputAction)

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR 

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[XML_READ_FUNCTION](/domino-c-api-docs/reference/Data/XML_READ_FUNCTION)
[XML_WRITE_FUNCTION](/domino-c-api-docs/reference/Data/XML_WRITE_FUNCTION)
[XSLTCreateTransform](/domino-c-api-docs/reference/Func/XSLTCreateTransform)
[XSLTRANSFORMHANDLE](/domino-c-api-docs/reference/Data/XSLTRANSFORMHANDLE)
---
