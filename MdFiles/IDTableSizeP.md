




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : ID Table**



**IDTableSizeP** **- Returns
the size of the specified ID Table in bytes.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



DWORD
LNPUBLIC **IDTableSizeP(**  

      void far \*pIDTable**);**



**Description :**



This
function takes a pointer to an ID Table, then calculates and returns the size
of the entire ID Table in bytes.  Since an ID Table contains header information
and is compressed, the size returned cannot be computed based on the number of
IDs in the table.


 


**Parameters :**



Input :  

pIDTable  -  Pointer to the ID Table.  

  




Output :  

(routine)  -  Returns the number of bytes occupied by the specified ID Table.  

  

  




 **See Also :**


**[IDTableSize](IDTableSize.md)**



----------------------------------------------------------------------------------------------------------


 





