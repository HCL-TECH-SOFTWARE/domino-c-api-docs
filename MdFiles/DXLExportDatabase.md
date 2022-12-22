




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



**DXLExportDatabase** **- DXL
export database**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



STATUS
LNPUBLIC **DXLExportDatabase(**  

      DXLEXPORTHANDLE  hDXLExport,  

      XML\_WRITE\_FUNCTION  pDXLWriteFunc,  

      DBHANDLE  hDB,  

      void far \*pExAction**);**



**Description :**



This
function allows the ability to export a full Domino Database into XML format.


 


**Parameters :**



Input :  

hDXLExport  -  allocated DXL export Handle, allocated calling the function
DXLCreateExporter(..)  

  

pDXLWriteFunc  -  The routine which is called once for each block of data to be
written.  This routine is user defined.  

  

hDB  -  allocated handle to the Domino database that is to be exported  

  

pExAction  -  user defined parameter passed to the XML\_WRITE\_FUNCTION.  This
data can be a means for keeping track of information during the export
process.  For example a structure can be defined that can keep track of the
amount of data exported and information on the exported file if the exported
data is to be written to a file.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully exported this Database into XML format.  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  




 **See Also :**


**[DBHANDLE](DBHANDLE.md)**


**[DXLEXPORTHANDLE](DXLEXPORTHANDLE.md)**


**[XML\_WRITE\_FUNCTION](XML_WRITE_FUNCTION.md)**



----------------------------------------------------------------------------------------------------------


 





