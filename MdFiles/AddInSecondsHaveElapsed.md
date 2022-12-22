




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




 


**Function : AddIn**



**AddInSecondsHaveElapsed** **- Determine
if a number of seconds has elapsed.**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



BOOL
LNPUBLIC **AddInSecondsHaveElapsed(**  

      DWORD  Seconds**);**



**Description :**



AddInSecondsHaveElapsed
is used to schedule processing at regular intervals.  Correct operation of this
function depends on AddInIdle being called regularly.  


 


      The
algorithm used is as follows:  

     Let itime = the time at which the Add-In program was started  

     Let mins = the specified # of minutes (argument 1)  

     Let stime = the earliest time after itime that is evenly divisible by
seconds.  

Then, this routine will return TRUE if the current time is later then stime,
FALSE otherwise.


 


**Parameters :**



Input :  

Seconds  -  The time interval to check for in seconds.  

  




Output :  

(routine)  -  TRUE if the specified interval (in seconds) has elapsed.  

  

  




 **Sample Usage :**


  

      else if (AddInSecondsHaveElapsed(20))  

       {  

           /\* Execute the "every 20 seconds" instructions \*/  

           sec\_double += 20.0;  

           AddInSetStatus(MSG\_SMKADDN\_TWENTYSECOND, 0L);  

           AddInFormatError(error\_msg, MSG\_SMKADDN\_TWENTYSECOND, 0L);  

           AddInLogMsg(MSG\_SMKADDN\_NAMESTUB, error\_msg);  

           DosSleep(5000L);  

  

           /\* Create a 3 string arg error\_msg from 3 numeric values\*/  

           sprintf(scratch\_str1, "%lf", day\_double);  

           sprintf(scratch\_str2, "%lf", min\_double);  

           sprintf(scratch\_str3, "%lf", sec\_double/20.0);  

           AddInFormatError(error\_msg, MSG\_SMKADDN\_STATS,  

                           scratch\_str1, scratch\_str2, scratch\_str3);  

           AddInLogMsg(MSG\_SMKADDN\_NAMESTUB, error\_msg);  

       }  

   


 **See Also :**


**[AddInIdle](AddInIdle.md)**


**[AddInDayHasElapsed](AddInDayHasElapsed.md)**


**[AddInShouldTerminate](AddInShouldTerminate.md)**


**[AddInMinutesHaveElapsed](AddInMinutesHaveElapsed.md)**



----------------------------------------------------------------------------------------------------------


 





