




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



**DXLGetImporterProperty** **- Get DXL
importer property**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



STATUS
LNPUBLIC **DXLGetImporterProperty(**  

      DXLIMPORTHANDLE  hDXLImporter,  

      DXL\_IMPORT\_PROPERTY  prop,  

      void \*retPropValue**);**



**Description :**



This
function retrieves the current set value of the Import Property Values defined
in DXL\_IMPORT\_PROPERTY.   Call this function for each property value to
retrieve.


 


**Parameters :**



Input :  

hDXLImporter  -  allocated DXL Import Handle, allocated calling the function
DXLCreateImporter(..)  

  

prop  -  the Import Property Value to get  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully obtained the DXL Import Property information.  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  

retPropValue  -  the current set value of the Import Property  

  

  




 **See Also :**


**[DXLIMPORTHANDLE](DXLIMPORTHANDLE.md)**


**[DXLIMPORTOPTION](DXLIMPORTOPTION.md)**


**[DXLSetImporterProperty](DXLSetImporterProperty.md)**


**[DXL\_IMPORT\_PROPERTY](DXL_IMPORT_PROPERTY.md)**



----------------------------------------------------------------------------------------------------------


 





