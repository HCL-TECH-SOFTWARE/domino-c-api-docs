




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




 


**Data Type : Menu Add-In**



**NAMPROC** **-** Menu add-in
program's entry point.


**----------------------------------------------------------------------------------------------------------**



**#include
<addinmen.h>**



**Definition :**



typedef NAMRESULT
(LNCALLBACKPTR NAMPROC)(


   WORD Command,


   void far \*pParam);


 


**Description :**



This is the
data type of a menu add-in program's entry point


 **See Also :**


**[NAMRESULT](NAMRESULT.md)**


**[NAMM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/006E007C005700A585255DEA0077E6DB)**



----------------------------------------------------------------------------------------------------------


 





