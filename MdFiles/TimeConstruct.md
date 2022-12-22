




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




 


**Function : Time**



**TimeConstruct** **-
Constructs a TIMEDATE from its two components.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



void
LNPUBLIC **TimeConstruct(**  

      DWORD  Date,  

      DWORD  Time,  

      TIMEDATE far \*result**);**



**Description :**



This
function constructs a TIMEDATE from its two components (date and ticks since
midnight) with no time zone information.


 


**Parameters :**



Input :  

Date  -  Julian date.  

  

Time  -  Number of ticks since midnight.  

  




Output :  

(routine)  -  None  

  

  

result  -  Pointer to the returned TIMEDATE value.  

  




 **See Also :**


**[TimeExtractJulianDate](TimeExtractJulianDate.md)**


**[TimeExtractDate](TimeExtractDate.md)**



----------------------------------------------------------------------------------------------------------


 





