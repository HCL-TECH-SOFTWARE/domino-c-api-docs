




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 6**



**Function : XML**



**XSLTTransform** **- Transform
XML data**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



STATUS
LNPUBLIC **XSLTTransform(**  

      XSLTRANSFORMHANDLE  hXSLTransform,  

      XML\_READ\_FUNCTION  pXSL\_XMLInputFunc,  

      void far \*pXSL\_XMLInputAction,  

      XML\_READ\_FUNCTION  pXSL\_StylesheetInputFunc,  

      void far \*pXSL\_StylesheetInputAction,  

      XML\_WRITE\_FUNCTION  pXSL\_TransformOutputFunc,  

      void far \*pXSL\_TransformOutputAction**);**



**Description :**



This
function transforms the XML data as input into the desired format on output
based on the stylesheet provided.


 


**Parameters :**



Input :  

hXSLTransform  -  allocated XSLT Transform  handle, allocated calling the
function XSLTCreateTransform(..)  

  

  

pXSL\_XMLInputFunc  -  this is a user defined read function (XML\_READ\_FUNCTION)
supplying the XML data to be transformed  

  

pXSL\_XMLInputAction  -  a pointer to user defined data (optional) which will
get passed along to the XML\_READ\_FUNCTION (pXSL\_XMLInputFunc)  

  

pXSL\_StylesheetInputFunc  -  this is a user defined read function
(XML\_READ\_FUNCTION( supplying the Stylesheet to be used in the transformation  

  

pXSL\_StylesheetInputAction  -   pointer to user defined data (optional) which
will get passed along to the XML\_READ\_FUNCTION (pXSL\_StylesheetInputAction)  

  

pXSL\_TransformOutputFunc  -  this is a user defined write (XML\_WRITE\_FUNCTION)
function which will be called with the XML data that has been transformed   

  

pXSL\_TransformOutputAction  -  pointer to user defined data (optional) which
will get passed along to the XML\_WRITE\_FUNCTION (pXSL\_TransformOutputAction)  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR   

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[XML\_READ\_FUNCTION](XML_READ_FUNCTION.md)**


**[XML\_WRITE\_FUNCTION](XML_WRITE_FUNCTION.md)**


**[XSLTCreateTransform](XSLTCreateTransform.md)**


**[XSLTRANSFORMHANDLE](XSLTRANSFORMHANDLE.md)**



----------------------------------------------------------------------------------------------------------


 





