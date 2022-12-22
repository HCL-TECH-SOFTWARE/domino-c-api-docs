




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



**TimeDateCollate** **- Compares
two binary TIMEDATE values.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



int
LNPUBLIC **TimeDateCollate(**  

      const TIMEDATE far \*t1,  

      const TIMEDATE far \*t2**);**



**Description :**



This
function is similar to TimeDateCompare.  It compares two binary TIMEDATE values
and returns an integer result, but without regard to their time zone
components.  Generally, unlike TimeDateCompare,  it will not work for wildcards
(either of the dates is ANYDAY or if either of the times is ALLDAY).  It will
work however for equality even if wildcards are present.  This routine is
faster than TimeDateCompare


 


**Parameters :**



Input :  

t1  -   A pointer to a TIMEDATE structure containing the first binary value.  

  

t2  -  A pointer to a TIMEDATE structure containing the second binary value.  

  




Output :  

(routine)  -  Returns -1 if the first argument is less than second one, Zero
(0) if the first and second arguments are equal, and +1 if the first argument
is greater than the second one.  

  

  




 **See Also :**


**[TimeDateCompare](TimeDateCompare.md)**


**[TIMEDATE](TIMEDATE.md)**


**[TimeDateDifference](TimeDateDifference.md)**


**[TimeDateEqual](TimeDateEqual.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





