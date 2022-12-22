




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 5.0.3**



**Symbolic Value : Calendaring and
Scheduling; Views**



**VIEW\_CAL\_VALID\_xxx\_FORMATS** **-** Version mask
for VIEW\_CAL\_FORMAT\_XXX


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VIEW\_CAL\_VALID\_PRE\_503\_FORMATS      -  Mask for the
VIEW\_CAL\_FORMAT\_XXX values prior to version 5.0.3.  

  

      VIEW\_CAL\_VALID\_503\_FORMATS   -  Mask for the VIEW\_CAL\_FORMAT\_XXX values
of version 5.0.3.  

  




**Description :**



This mask
indicates the maximum of VIEW\_CAL\_FORMAT\_XXX values specified in the 
VIEW\_CALENDAR\_FORMAT.Formats item for different versions.


 **Sample Usage :**


The following code
checks the minor version of the calendar format and clear out any bit that was
not supported prior to verion 5.0.3:


 


 


if
(CalendarFormat.MinorVersion < VIEW\_CAL\_FORMAT\_MINOR\_2)


  
CalendarFormat.Formats &= VIEW\_CAL\_VALID\_PRE\_503\_FORMATS;


 


 **See Also :**


**[VIEW\_CALENDAR\_FORMAT](VIEW_CALENDAR_FORMAT.md)**


**[VIEW\_CAL\_FORMAT\_MINOR\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DF129000AC532F3B852566780073BD75)**


**[VIEW\_CAL\_FORMAT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CBEA16AD260C50DE8525636100758FF5)**



----------------------------------------------------------------------------------------------------------


 





