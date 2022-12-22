




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




 


**Function : Time**



**OSCurrentTIMEDATE** **- Gets the
system time/date.**


**----------------------------------------------------------------------------------------------------------**



**#include <ostime.h>**



void
LNPUBLIC **OSCurrentTIMEDATE(**  

      TIMEDATE far \*retTimeDate**);**



**Description :**



This
function gets the current system time and date, returning it in Domino binary
format.  The Domino binary time/date format is an internal format, and can only
be interpreted by using the C API time/date functions.


 


**Parameters :**




Output :  

(routine)  -  None.  

  

  

retTimeDate  -  The address of a TIMEDATE structure in which the current time
and date in Domino binary format is returned.  

  




 **Sample Usage :**


  

    OSCurrentTIMEDATE(&binary\_td1);   /\* Get current Time/Date values \*/  

  




 **See Also :**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**



----------------------------------------------------------------------------------------------------------


 





