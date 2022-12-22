




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




 


**Symbolic Value : Statistics
Reporting**



**ST\_xxx** **-** Flags for
StatUpdate.


**----------------------------------------------------------------------------------------------------------**



**#include <stats.h>**


 **Symbolic Values :**      ST\_UNIQUE             -  Statistic is unique - only one
instance is allowed.  

  

      ST\_ADDITIVE          -  Value type of statistic is VT\_LONG or VT\_NUMBER
and the new value is to be added to the current value of the statistic.  

  

      ST\_RESETABLE      -  Statistic is resetable to 0.  

  




**Description :**



These are
the values you may specify in the Flags parameter to StatUpdate(). Specify a
Flags value of 0 to prevent StatUpdate from taking any of these actions.


 **See Also :**


**[StatUpdate](StatUpdate.md)**



----------------------------------------------------------------------------------------------------------


 





