




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




**Initial Release 5.0**



**Data Type : Composite Data; Rich
Text; Table**



**CDCELLBACKGROUNDDATA** **-** Specifies
Table Background Data.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

    BYTE  Repeat;


    BYTE  Spare[1];


    DWORD SpareDWORD;


} CDCELLBACKGROUNDDATA;


 


**Description :**



This CD
Record gives information pertaining to Background Data for a Table,
specifically the 'Cell Image' repeat value.


 


Header                   Identifies
the record as a CDCELLBACKGROUNDDATA.


Repeat                   
see REPEAT\_xxx (Table background image settings (Repeat Once, Repeat
Vertically, Repeat Horizontally, Center, Size to Fit))


Spare[1]                 Not
Used.


SpareDWORD        Not
Used.


 


 **See Also :**


**[REPEAT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FB61B37C270C35578525672E007A6309)**



----------------------------------------------------------------------------------------------------------


 





