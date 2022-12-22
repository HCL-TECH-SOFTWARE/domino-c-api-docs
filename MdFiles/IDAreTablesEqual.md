




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




**Initial Release 4.5**



**Function : ID Table**



**IDAreTablesEqual** **- Determine
whether two ID Tables contain the same contents.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



BOOL   LNPUBLIC **IDAreTablesEqual(**  

      DHANDLE  hSrc1Table,  

      DHANDLE  hSrc2Table**);**



**Description :**



This
function compares two ID Tables and returns TRUE if they contain the same
contents.  Otherwise, FALSE is returned.  


 


You can pass
in NULLHANDLE for the handle of either of the ID Tables.  If both handles are
NULLHANDLE, then TRUE is returned.  Otherwise, FALSE is returned.


 


**Parameters :**



Input :  

hSrc1Table  -  Handle to the first of two ID Tables that will be compared.  

  

hSrc2Table  -  Handle to the second of two ID Tables that will be compared.  

  




Output :  

(routine)  -  TRUE if the two ID Tables contain the same contents, FALSE
otherwise.  

  

  




 **See Also :**


**[IDCreateTable](IDCreateTable.md)**


**[IDTableIntersect](IDTableIntersect.md)**


**[IDDeleteTable](IDDeleteTable.md)**


**[IDInsertTable](IDInsertTable.md)**



----------------------------------------------------------------------------------------------------------


 





