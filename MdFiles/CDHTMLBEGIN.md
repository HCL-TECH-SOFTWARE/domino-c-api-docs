




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




**Initial Release 4.6**



**Data Type : Rich Text; Composite
Data**



**CDHTMLBEGIN** **-** Start of
pass-through HTML text.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG Header;  

   BYTE Spares[4];  

} CDHTMLBEGIN;


 


**Description :**



Text in a
rich-text field can have the "Pass-Thru HTML" attribute. 
Pass-through HTML text is not translated to the Domino rich text format. 
Pass-through HTML text is marked by CDHTMLBEGIN and CDHTMLEND records.


 


The fields
in this structure are:


 


Header             Identifies
this as a CDHTMLBEGIN record.


Spares             Reserved; 
must be 0.


 


 **See Also :**


**[CDHTMLEND](CDHTMLEND.md)**



----------------------------------------------------------------------------------------------------------


 





