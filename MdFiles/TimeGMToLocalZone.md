




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



**TimeGMToLocalZone** **- Expand
TIMEDATE using another time zone value.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



BOOL
LNPUBLIC **TimeGMToLocalZone(**  

      TIME far \*Time**);**



**Description :**



This
function takes the binary TIMEDATE structure and a specific time zone and DST
setting, and converts it into its constituent components, and assigns those
values to the appropriate (int) members of the TIME structure.   This can be
used to convert a time to a given time zone.  The TimeGMToLocalZone and TimeLocalToGM
pairing can be used to convert any TIMEDATE from one time zone to another.  

  

Note:  If the TIMEDATE that is to be expanded contains only a date, and not a
time, then you will need to set the time component ALLDAY in order to use this
function.


 


**Parameters :**



Input :  

Time  -  A pointer to a TIME structure whose time\_ptr->GM member contains
the TIMEDATE structure you wish to expand, and whose Time->zone and
Time->dst are the desired time zone and DST setting.  

  




Output :  

(routine)  -  Returns FALSE if successful and TRUE if not.  

  

  

Time  -  The address of the TIME structure in which the constituent (int)
values of the Time->GM member are returned.  

  




 **Sample Usage :**


/\* Convert from GMT to
a local time zone the easy way \*/  

time\_seqnum.GM.Innards[0] = note\_sequence\_td.Innards[0];  

time\_seqnum.GM.Innards[1] = note\_sequence\_td.Innards[1];  

if (TimeGMToLocalZone(&time\_seqnum))  

   goto Exit;  

  

/\* convert the (int) members back to the GM member \*/  

if (TimeLocalToGM(&time\_seqnum))  

   goto Exit;


 **See Also :**


**[TimeGMToLocal](TimeGMToLocal.md)**


**[TimeLocalToGM](TimeLocalToGM.md)**


**[OSCurrentTimeZone](OSCurrentTimeZone.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





