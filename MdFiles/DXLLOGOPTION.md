




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**Data Type : XML**



**DXLLOGOPTION** **-** DXL Import
Options for log reporting


**----------------------------------------------------------------------------------------------------------**



**#include
<xml.h>**



**Definition :**



typedef enum


{


        DXLLOGOPTION\_IGNORE=1,        /\*
ignore the action.  don't log anything and just continue \*/


        DXLLOGOPTION\_WARNING=2,               /\*
log the problem as a warning \*/


        DXLLOGOPTION\_ERROR=3,         /\*
log the problem as an error \*/


        DXLLOGOPTION\_FATALERROR=4             /\*
log the problem as a fatal error \*/


 


}
DXLLOGOPTION; 


 


**Description :**



Values to
set DXL\_IMPORT\_PROPERTY member iUnknownTokenLogOption.  


 **See Also :**


**[DXLGetImporterProperty](DXLGetImporterProperty.md)**


**[DXLSetImporterProperty](DXLSetImporterProperty.md)**


**[DXL\_IMPORT\_PROPERTY](DXL_IMPORT_PROPERTY.md)**



----------------------------------------------------------------------------------------------------------


 





