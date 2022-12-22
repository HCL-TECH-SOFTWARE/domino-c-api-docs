




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




 


**Data Type : Time**



**TIMEDATE\_PAIR** **-** A range of
time in Domino binary format.


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



typedef struct {  

   TIMEDATE Lower;  

   TIMEDATE Upper;  

} TIMEDATE\_PAIR;


 


**Description :**



This
structure represents a range of time in Domino binary format. The elements of
this structure only should be interpreted using the C API time/date calls --
they cannot easily be parsed directly.


 **See Also :**


**[ConvertTextToTIMEDATEPAIR](ConvertTextToTIMEDATEPAIR.md)**


**[ConvertTIMEDATEPAIRToText](ConvertTIMEDATEPAIRToText.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**


**[TYPE\_xxx [TIME\_RANGE]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C598A7AE1C5A2C6A8525622E00645C02)**



----------------------------------------------------------------------------------------------------------


 





