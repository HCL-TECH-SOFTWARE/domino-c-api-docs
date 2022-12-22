




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



**AddInMinutesHaveElapsed** **- Determine
if a number of minutes has elapsed.**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



BOOL
LNPUBLIC **AddInMinutesHaveElapsed(**  

      DWORD  Minutes**);**



**Description :**



AddInMinutesHaveElapsed
is used to schedule processing at regular intervals.  Correct operation of this
function depends on AddInIdle being called regularly.  The algorithm used is as
follows:  

     Let itime = the time at which the Add-In program was started  

     Let mins = the specified # of minutes (argument 1)  

     Let stime = the earliest time after itime that is evenly divisible by
mins.  

Then, this routine will return TRUE if the current time is later then stime,
FALSE otherwise.  

  

It is implemented as macro using AddInSecondsHaveElapsed:  

#define AddInMinutesHaveElapsed(x) AddInSecondsHaveElapsed((DWORD)(x)\*60L)


 


**Parameters :**



Input :  

Minutes  -  The time interval to check for, in minutes.  

  




Output :  

(routine)  -  TRUE if the specified number of minutes has elapsed.  See long
description for a definition of the algorithm used.  

  

  




 **Sample Usage :**


else if
(AddInMinutesHaveElapsed(1))  

{  

  /\* Execute the "every minute" instructions \*/  

  min\_double += 1.0;  

  AddInSetStatus(MSG\_SMKADDN\_ONEMINUTE, 0L);  

  AddInFormatError(error\_msg, MSG\_SMKADDN\_ONEMINUTE, 0L);  

  AddInLogMsg(MSG\_SMKADDN\_NAMESTUB, error\_msg);  

  DosSleep(5000L);  

  

  /\* Create a 3 string arg error\_msg from 3 numeric values\*/  

  sprintf(scratch\_str1, "%lf", day\_double);  

  sprintf(scratch\_str2, "%lf", min\_double);  

  sprintf(scratch\_str3, "%lf", sec\_double/20.0);  

  AddInFormatError(error\_msg, MSG\_SMKADDN\_STATS,  

                   scratch\_str1, scratch\_str2, scratch\_str3);  

  AddInLogMsg(MSG\_SMKADDN\_NAMESTUB, error\_msg);  

  if (min\_double > 1L)  

  {  

    /\* There might be several minutes worth of import    \*/  

    /\* activity initiated here and AddInShouldTerminate()\*/  

    /\* calls could be blended in among buffered I/O calls\*/  

    if(AddInShouldTerminate())  

      break;  

    /\* Application shuts itself off after 5 minutes     \*/  

    /\* A "Program" note in the server's Name & Address  \*/  

    /\* Book could be used to restart this AddIn on a    \*/  

    /\* regularly scheduled basis.                       \*/  

    else if(min\_double == 5L)  

      break;  

  }  

}


 **See Also :**


**[AddInSecondsHaveElapsed](AddInSecondsHaveElapsed.md)**


**[AddInDayHasElapsed](AddInDayHasElapsed.md)**


**[AddInIdle](AddInIdle.md)**



----------------------------------------------------------------------------------------------------------


 





