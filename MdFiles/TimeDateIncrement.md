




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



**TimeDateIncrement** **- Increment
binary TIMEDATE value.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **TimeDateIncrement(**  

      TIMEDATE far \*Time,  

      LONG  Interval**);**



**Description :**



This
function increments the contents of a TIMEDATE structure using the specified
increment.  The value of the increment is taken as being in 10 millisecond
units.


 


**Parameters :**



Input :  

Time  -  A pointer to a TIMEDATE structure containing the Time/Date you wish to
increment.  

  

Interval  -  LONG containing positive increment in 10 millisecond units.  100L
= 1 sec, 1000L = 10 sec, and 6000L = 1 minute.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:   

  

NOERROR - Incrementing operation was successful .  

ERR\_TREQ - TIME must be specified, not just DATE.  The TIMEDATE stucture
provided was set to the TIMEDATE\_WILDCARD (more specifically, the Innards[0]
member of this structure was set to ALLDAY, which is usually used as a
wild-card in database operations).  

  

  

Time  -  The address of  the TIMEDATE structure in which the original value,
plus the increment is returned.  

  




 **Sample Usage :**


  

   /\* Increment the copy by a given interval in (10ms units)       \*/  

  

   time\_increment = 6000L;       /\* increment TimeDate by 60 secs  \*/  

   if (error\_status = TimeDateIncrement(&binary\_td2, time\_increment))  

       goto Exit;  

  

  




 **See Also :**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





