




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




**Initial Release 6.0.1**



**Function : Time**



**OSGetExtIntlFormat** **- Get
international format extended.**


**----------------------------------------------------------------------------------------------------------**



**#include <intl.h>**



WORD
LNPUBLIC **OSGetExtIntlFormat(**  

      char  item,  

      char  index,  

      void \*buff,  

      WORD  bufSize**);**



**Description :**



This
function will retrieve the international format of various operating system
time and date attributes.


 


**Parameters :**



Input :  

item  -  The item you want to retrieve.  See: ABBRERANAME, ABBR\_MONTH\_NAMES,
ABBR\_WEEKDAY\_NAMES, CALENDARTYPE, CALENDAR\_xxx, ERANAME, EXT\_xxx, MONTH\_NAMES,
WEEKDAY\_NAMES.  

  

index  -  Index for month (1-12) or weekday (1-7) names.  

  

bufSize  -  Size of output buffer  

  




Output :  

(routine)  -  Ouput string length.  

  

  

buff  -  Output buffer.  

  




 **See Also :**


**[ABBRERANAME](ABBRERANAME.md)**


**[ABBR\_MONTH\_NAMES](ABBR_MONTH_NAMES.md)**


**[ABBR\_WEEKDAY\_NAMES](ABBR_WEEKDAY_NAMES.md)**


**[CALENDARTYPE](CALENDARTYPE.md)**


**[CALENDAR\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/417B689B8AB7C3CF85256C6B0072B0AE)**


**[ERANAME](ERANAME.md)**


**[EXT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5F7896888A4111D685256C6B0071BF5B)**


**[MONTH\_NAMES](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/8C9D66F7B649C2D585256C6B0071FB99)**


**[WEEKDAY\_NAMES](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/15F8BA44A754801D85256C6B00724FE6)**



----------------------------------------------------------------------------------------------------------


 





