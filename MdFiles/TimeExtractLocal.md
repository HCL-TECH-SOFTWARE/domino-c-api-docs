




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



**TimeExtractLocal** **- Converts
a TIMEDATE value to just a time or a date.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



void
LNPUBLIC **TimeExtractLocal(**  

      const TIMEDATE far \*Time,  

      BOOL  fTime,  

      TIMEDATE far \*retTime**);**



**Description :**



This
function converts a TIMEDATE value to just a time or date in the local time
zone, even if one of the components happens to be a wildcard (ANYDAY or
ALLDAY).


 


**Parameters :**



Input :  

Time  -  Pointer to TIMEDATE value to be extracted.  

  

fTime  -  Use TRUE to extract the time, FALSE to extract the date.  

  




Output :  

(routine)  -  None  

  

  

retTime  -  Extracted TIMEDATE value.  

  




 **See Also :**


**[TIMEDATE](TIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





