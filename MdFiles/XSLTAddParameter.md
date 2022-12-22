




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



**XSLTAddParameter** **- Set XSLT
parameter value(s)**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



STATUS
LNPUBLIC **XSLTAddParameter(**  

      XSLTRANSFORMHANDLE  hXSLTransform,  

      const char \*szParmName,  

      const char \*szParmValue**);**



**Description :**



This
function allows the ablitity to set parameter value(s) before calling the
function XSLTTransform(..).   


 


**Parameters :**



Input :  

hXSLTransform  -  allocated XSLT Transform  handle, allocated calling the
function XSLTCreateTransform(..)  

  

szParmName  -  the parameter name to set  

  

szParmValue  -  the value of the parameter to be set  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR   

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[XSLTCreateTransform](XSLTCreateTransform.md)**


**[XSLTRANSFORMHANDLE](XSLTRANSFORMHANDLE.md)**


**[XSLTTransform](XSLTTransform.md)**



----------------------------------------------------------------------------------------------------------


 





