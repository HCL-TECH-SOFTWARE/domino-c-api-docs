




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



**XSLTCreateTransform** **- Create an
XSLT Transform Handle.**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



STATUS
LNPUBLIC **XSLTCreateTransform(**  

      XSLTRANSFORMHANDLE \*prethXSLTransform**);**



**Description :**



This
function is called to initialize both the XSLTRANSFORMHANDLE and the
XSLT\_PROPERTY default values.  This function  must be the first function called
when setting up an XSLT Tranform.


 


**Parameters :**



Input :  

prethXSLTransform  -  An XSLT Transform Handle which is needed to pass to the
other XSLT functions.   

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR   

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[XSLTRANSFORMHANDLE](XSLTRANSFORMHANDLE.md)**


**[XSLTTransformDeleteTransform](XSLTTransformDeleteTransform.md)**


**[XSLT\_PROPERTY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3C3B0B41F7C4835085256C2B004FD179)**



----------------------------------------------------------------------------------------------------------


 





