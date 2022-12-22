




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



**TimeDateCompare** **- Compares
two binary TIMEDATE values.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



int
LNPUBLIC **TimeDateCompare(**  

      const TIMEDATE far \*t1,  

      const TIMEDATE far \*t2**);**



**Description :**



This
function normalizes each argument to the same time zone, and compares the two
binary TIMEDATE values and returns an integer result.


 


**Parameters :**



Input :  

t1  -  A pointer to a TIMEDATE structure containing the first binary value.  

  

t2  -  A pointer to a TIMEDATE structure containing the second binary value.  

  




Output :  

(routine)  -  Returns -1 if the first argument is less than second one, Zero
(0) if the first and second arguments are equal, and +1 if the first argument
is greater than the second one.  

  

  




 **Sample Usage :**


     

   td\_compare\_result = TimeDateCompare(&binary\_td2,&binary\_td3);  

  




 **See Also :**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**


**[TimeDateCollate](TimeDateCollate.md)**


**[TimeDateEqual](TimeDateEqual.md)**


**[TimeDateDifference](TimeDateDifference.md)**


**[TIMEDATE](TIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





