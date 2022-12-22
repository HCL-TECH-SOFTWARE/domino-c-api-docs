




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



**TimeDateEqual** **- Returns
whether two TIMEDATE values are equal.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



BOOL **TimeDateEqual(**  

      TIMEDATE far \*t1,  

      TIMEDATE far \*t2**);**



**Description :**



This is a
macro which returns TRUE if two TIMEDATE values are equal and FALSE if
otherwise.  The time zone components are ignored.


 


**Parameters :**



Input :  

t1  -  A pointer to a TIMEDATE structure containing the first binary value.  

  

t2  -  A pointer to a TIMEDATE structure containing the second binary value .  

  




Output :  

(routine)  -  TRUE if the TIMEDATE values are the same (the time zone
components are ignored), otherwise FALSE  

  

  




 **See Also :**


**[TIMEDATE](TIMEDATE.md)**


**[TimeDateCollate](TimeDateCollate.md)**


**[TimeDateCompare](TimeDateCompare.md)**


**[TimeDateDifference](TimeDateDifference.md)**



----------------------------------------------------------------------------------------------------------


 





