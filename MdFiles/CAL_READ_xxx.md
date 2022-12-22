




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




**Initial Release 9.0**



**Symbolic Value : iCalendar**



**CAL\_READ\_xxx** **-** Flags that
control behavior of the calendar APIs that return iCalendar data for an entry
or notice


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**


 **Symbolic Values :**      CAL\_READ\_HIDE\_X\_LOTUS            -  By default, some X-LOTUS
properties and parameters will be included in iCalendar data returned by these
APIs. CAL\_READ\_HIDE\_X\_LOTUS causes all X-LOTUS properties and parameters to be
removed from the generated iCalendar data.  

Note: This overrides CAL\_READ\_INCLUDE\_X\_LOTUS  

  

      CAL\_READ\_INCLUDE\_X\_LOTUS     -  Include all Lotus specific properties
like X-LOTUS-UPDATE-SEQ, X-LOTUS-UPDATE\_WISL, etc in the generated iCalendar
data.These properties are NOT included by default in any iCalendar data returned
by the APIs.  

Caution: Unless the caller knows how to use these it can be dangerous since
their presence will be honored and can cause issues if not updated properly.  

Ignored if CAL\_READ\_HIDE\_X\_LOTUS is also specified.  

  




 




----------------------------------------------------------------------------------------------------------


 





