




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



**AddInDayHasElapsed** **- Return
TRUE once a day.**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



BOOL
LNPUBLIC **AddInDayHasElapsed(**void**);**



**Description :**



AddInDayHasElapsed
is used primarily to check for when it is time to do daily housekeeping
chores.  The routine will return TRUE the first time it is called after the
AddIn has started, and then once each day (at 2:00 AM GMT) thereafter.    

  

Note: the routine AddInIdle must also be called regularly (at least as often as
this API is called) in order for this API to work properly.  

  




 


**Parameters :**




Output :  

(routine)  -  TRUE the first time the routine is called, and thereafter, TRUE if
it is the first call after 2:00 AM Greenwich Mean Time  (GMT) since the last
time the routine returned TRUE.  FALSE otherwise.  

  

  




 **Sample Usage :**


  

       if (AddInDayHasElapsed())  

       {  

           day\_double += 1.0;  

           /\* Execute the "daily" instructions \*/  

           AddInSetStatus(MSG\_SMKADDN\_ONCEADAY, 0L);  

           AddInFormatError(error\_msg, MSG\_SMKADDN\_ONCEADAY, 0L);  

           AddInLogMsg(MSG\_SMKADDN\_NAMESTUB, error\_msg);  

           DosSleep(5000L);  

  

           /\* Create a 3 string arg error\_msg from 3 numeric values\*/  

           sprintf(scratch\_str1, "%lf", day\_double);  

           sprintf(scratch\_str2, "%lf", min\_double);  

           sprintf(scratch\_str3, "%lf", sec\_double/20.0);  

           AddInFormatError(error\_msg, MSG\_SMKADDN\_STATS,  

                          scratch\_str1, scratch\_str2, scratch\_str3);  

           AddInLogMsg(MSG\_SMKADDN\_NAMESTUB, error\_msg);  

           sprintf(item\_name, "%s", "AddInEvents");  

           if (error\_status = LogAddTextlistItem(log\_entry,  

                                            LOG\_LEAVE\_LOCKED,  

                                            item\_name, error\_msg))  

               goto Exit;  

       }


 **See Also :**


**[AddInIdle](AddInIdle.md)**


**[AddInSecondsHaveElapsed](AddInSecondsHaveElapsed.md)**


**[AddInMinutesHaveElapsed](AddInMinutesHaveElapsed.md)**


**[AddInShouldTerminate](AddInShouldTerminate.md)**



----------------------------------------------------------------------------------------------------------


 





