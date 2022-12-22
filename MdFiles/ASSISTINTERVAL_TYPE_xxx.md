




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




**Initial Release 4.5**



**Symbolic Value : Agents**



**ASSISTINTERVAL\_TYPE\_xxx** **-** ODS\_ASSISTSTRUCT
- wIntervalType values for agent interval types.


**----------------------------------------------------------------------------------------------------------**



**#include <queryods.h>**


 **Symbolic Values :**      ASSISTINTERVAL\_TYPE\_NONE      -  No interval type specified.  

  

      ASSISTINTERVAL\_TYPE\_MINUTES            -  The wInterval field contains
the interval between invocations in minutes. dwTime1 contains the local time of
the day when the Agent should start execution, and dwTime2 contains the local
time of day after which the Agent should not be executed. dwTime1 and dwTime2 are
specified in 10-millisecond "ticks" since local midnight.  

  

      ASSISTINTERVAL\_TYPE\_DAYS      -  The wInterval field contains the
interval between invocations in days. dwTime1 contains the local time of the
day when the Agent should be run, specified in 10-millisecond "ticks"
since local midnight. dwTime2 is not used.  

  

      ASSISTINTERVAL\_TYPE\_WEEK     -  The wInterval field contains the interval
between invocations in weeks. dwTime1 contains the local time of the day when
the Agent should be run, specified in 10-millisecond "ticks" since
local midnight. dwTime2 contains an integer from 0 to 6 specifying the day of
the week when the Agent should be run.  

  

      ASSISTINTERVAL\_TYPE\_MONTH   -  The wInterval field contains the interval
between invocations in months. dwTime1 contains the local time of the day when
the Agent should be run, specified in 10-millisecond "ticks" since
local midnight. dwTime2 contains an integer from 0 to 31 specifying the day of
the month when the Agent should be run.  

  

      ASSISTINTERVAL\_TYPE\_EVENT    -  The wInterval field contains the interval
between invocations of eventss. dwTime1 contains the local time of the day when
the Agent should be run, specified in 10-millisecond "ticks" since
local midnight. dwTime2 is not used.  

  




**Description :**



The interval
type codes are stored in the wIntervalType field of the ODS\_ASSISTSTRUCT for an
Agent.  The interval type code determines the intrepretation of the wInterval,
dwTime1, and dwTime2 fields in the structure.


 **See Also :**


**[ODS\_ASSISTSTRUCT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/540A215A94BACC0385256261006222BC)**



----------------------------------------------------------------------------------------------------------


 





