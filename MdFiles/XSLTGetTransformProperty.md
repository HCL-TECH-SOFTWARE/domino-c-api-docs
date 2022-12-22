




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



**XSLTGetTransformProperty** **- Get an
XSLT Tranform Property Value**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



STATUS
LNPUBLIC **XSLTGetTransformProperty(**  

      XSLTRANSFORMHANDLE  hXSLTransform,  

      XSLT\_PROPERTY  prop,  

      void \*retPropValue**);**



**Description :**



This
function retrieves the current set value of the XSLT Property Values defined in
XSLT\_PROPERTY.   Call this function for each property value to retrieve.


 


**Parameters :**



Input :  

hXSLTransform  -  allocated XSLT Tranform Handle, allocated calling the
function XSLTCreateTransform(..)  

  

prop  -  the XSLT property value to get  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR   

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retPropValue  -  the current set value of this XSLT Property member  

  




 **See Also :**


**[XSLTCreateTransform](XSLTCreateTransform.md)**


**[XSLTRANSFORMHANDLE](XSLTRANSFORMHANDLE.md)**


**[XSLT\_PROPERTY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3C3B0B41F7C4835085256C2B004FD179)**



----------------------------------------------------------------------------------------------------------


 





