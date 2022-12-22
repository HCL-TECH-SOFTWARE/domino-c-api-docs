




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Data Type : Views**



**IXCOLUMNTEXTDESC** **-** Formatted
column text descriptor.


**----------------------------------------------------------------------------------------------------------**



**#include
<ixview.h>**



**Definition :**



typedef struct {  

   WORD Width;             /\* Column width in 1/8 characters \*/  

   WORD Position;          /\* Column position in characters \*/  

   FLAG Alignment:2;       /\* Alignment (left, right, etc. ) \*/  

   FLAG LastColumn:1;      /\* Last column flag \*/  

   FLAG Category:1;        /\* Column is a category flag \*/  

   WORD TextMax;           /\* Text space allocated for this column \*/  

   WORD TextLength;        /\* Text string length \*/  

/\* char Text[TextMax]; \*/ /\* Text string itself \*/  

} IXCOLUMNTEXTDESC;


 


**Description :**



This is a
data structure used to store text information extracted from the NIF Summary
information for exports of view data into text.


 **See Also :**


**[IXCOLDESC](IXCOLDESC.md)**



----------------------------------------------------------------------------------------------------------


 





