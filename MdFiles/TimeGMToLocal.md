




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



**TimeGMToLocal** **- Convert
TIMEDATE to year, month, day, etc..**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



BOOL
LNPUBLIC **TimeGMToLocal(**  

      TIME far \*Time**);**



**Description :**



This
function takes a TIME structure, converts the .GM member (binary TIMEDATE) into
its constituent components, and assigns those values to the appropriate integer
members of the same TIME structure.   

  

It is useful in bridging to data structures required by Operating Systems or
'C' library time/date functions or in the process of converting a TIMEDATE
value from one time zone to its equivalent value in an other time zone.


 


**Parameters :**



Input :  

Time  -  A pointer to a TIME structure whose Time->GM member contains the
TIMEDATE structure you wish to expand.  

  




Output :  

(routine)  -  Returns FALSE if successful and TRUE if not.  

  

  

Time  -  The address of the TIME struture in which the constituent values of
the Time->GM member are returned.  

  




 **Sample Usage :**


time\_oid.GM =
note\_created\_td;  

if (TimeGMToLocal(&time\_oid))  

   goto Exit;


 **See Also :**


**[TimeLocalToGM](TimeLocalToGM.md)**


**[TimeGMToLocalZone](TimeGMToLocalZone.md)**


**[OSCurrentTimeZone](OSCurrentTimeZone.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





