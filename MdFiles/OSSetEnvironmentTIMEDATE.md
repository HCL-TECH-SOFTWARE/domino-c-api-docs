




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




 


**Function : OS Environment Variables**



**OSSetEnvironmentTIMEDATE** **- Set a
given environment variable to a provided TIMEDATE value.**


**----------------------------------------------------------------------------------------------------------**



**#include <osenv.h>**



void **OSSetEnvironmentTIMEDATE(**  

      const char \*EnvVariable,  

      TIMEDATE \*td**);**



**Description :**



Set a
TIMEDATE for an environment variable. This routine writes the given TIMEDATE
into the given environment variable. If NULL is provided for a value to set,
the current TIMEDATE is sent the to the given environment variable.


 


**Parameters :**



Input :  

EnvVariable  -  Name of environment variable (ASCIZ).  

  

td  -  TIMEDATE  to set.  

  




 


 **Sample Usage :**


      /\*
LastWeekFriday is a TIMEDATE set to a date in the past, say.\*/ 


 


            OSSetEnvironmentTIMEDATE
("LAST\_FRIDAY\_DATE", &LastWeekFriday); 


            OSSetEnvironmentTIMEDATE
("TODAY\_DATE", NULL); 


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





