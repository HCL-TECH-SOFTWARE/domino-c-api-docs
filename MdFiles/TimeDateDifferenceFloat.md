




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



**TimeDateDifferenceFloat** **-
Floating-point difference between two TIMEDATE values.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



void
LNPUBLIC **TimeDateDifferenceFloat(**  

      const TIMEDATE far \*t1,  

      const TIMEDATE far \*t2,  

      NUMBER far \*difference**);**



**Description :**



This
function returns a double value containing the difference in seconds between
two TIMEDATE values.  The values are normalized to a common time zone for the
calculation.  If the first argument is greater than the second, the returned
value is positive.  If the first argument is smaller than the second, the
returned value is negative.  


 


**Parameters :**



Input :  

t1  -  A pointer to a TIMEDATE structure containing the first binary value.  

  

t2  -  A pointer to a TIMEDATE structure containing the second binary value.  

  




Output :  

difference  -  Address where the floating-point result is to be stored.  The
difference is in seconds.  

  




 **Sample Usage :**


  

   /\* Obtain the difference in SECONDS between two TIMEDATEs       \*/  

  

   NUMBER time\_delta;  

  

   TimeDateDifferenceFloat(&binary\_td2,&binary\_td1, &time\_delta);  
  

  




 **See Also :**


**[TimeDateAdjust](TimeDateAdjust.md)**


**[TimeDateCompare](TimeDateCompare.md)**


**[TimeDateDifference](TimeDateDifference.md)**


**[TimeDateIncrement](TimeDateIncrement.md)**



----------------------------------------------------------------------------------------------------------


 





