




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



**DXLCreateImporter** **- Create
DXL importer**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



STATUS
LNPUBLIC **DXLCreateImporter(**  

      DXLIMPORTHANDLE \*prethDXLImport**);**



**Description :**



This
function initializes both the DXLIMPORTHANDLE and the DXL\_IMPORT\_PROPERTY
default values.  This function must be the first function called prior to
importing Domino XML data.  


 


 


**Parameters :**



Input :  

prethDXLImport  -  A DXL Import Handle needed to pass to the other DXL Import
functions.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully allocated the DXLIMPORTHANDLE.  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  




 **See Also :**


**[DXLDeleteImporter](DXLDeleteImporter.md)**


**[DXLIMPORTHANDLE](DXLIMPORTHANDLE.md)**


**[DXL\_IMPORT\_PROPERTY](DXL_IMPORT_PROPERTY.md)**



----------------------------------------------------------------------------------------------------------


 





