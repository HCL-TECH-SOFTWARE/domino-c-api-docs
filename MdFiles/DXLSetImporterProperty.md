




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



**DXLSetImporterProperty** **- Set DXL
importer property**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



STATUS
LNPUBLIC **DXLSetImporterProperty(**  

      DXLIMPORTHANDLE  hDXLImport,  

      DXL\_IMPORT\_PROPERTY  prop,  

      void \*propValue**);**



**Description :**



This
function sets the Import Property Values defined in DXL\_IMPORT\_PROPERTY.  Call
this function for each property value to set.


 


 


**Parameters :**



Input :  

hDXLImport  -  allocated DXL Import Handle, allocated calling the function
DXLCreateImporter(..)  

  

  

prop  -  the Import Property to set  

  

propValue  -  value to set the Import Property, values defined in
DXL\_IMPORT\_PROPERTY  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully set the import property value..  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  




 **See Also :**


**[DXLGetImporterProperty](DXLGetImporterProperty.md)**


**[DXLIMPORTHANDLE](DXLIMPORTHANDLE.md)**


**[DXLIMPORTOPTION](DXLIMPORTOPTION.md)**


**[DXL\_IMPORT\_PROPERTY](DXL_IMPORT_PROPERTY.md)**



----------------------------------------------------------------------------------------------------------


 





