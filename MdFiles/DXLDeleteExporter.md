




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



**DXLDeleteExporter** **- Delete
DXL exporter**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



void
LNPUBLIC **DXLDeleteExporter(**  

      DXLEXPORTHANDLE  hDXLExport**);**



**Description :**



This
function unlocks and frees the DXLEXPORTHANDLE.  This function must be called
to free up memory allocated by DXLCreateExporter.


 


**Parameters :**



Input :  

hDXLExport  -  the allocated DXL Export Handle  

  




Output :  

(routine)  -  None.  

  

  




 **See Also :**


**[DXLCreateExporter](DXLCreateExporter.md)**


**[DXLEXPORTHANDLE](DXLEXPORTHANDLE.md)**



----------------------------------------------------------------------------------------------------------


 





