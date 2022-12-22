




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



**AddInIdle** **- Yield
processor and check if termination required.**


**----------------------------------------------------------------------------------------------------------**



**#include <addin.h>**



BOOL
LNPUBLIC **AddInIdle(**void**);**



**Description :**



Use this
function to control the main loop of a custom Lotus Domino Server add-in task.
AddInIdle suspends the calling task and gives control to Domino. AddInIdle
returns FALSE to indicate that the add-in task should continue.  AddInIdle
returns TRUE when the add-in task should terminate, normally after the Lotus
Domino Server receives a "quit", "tell <taskname>
quit", or "exit" command.  Add-in tasks must call AddInIdle in
the main loop in order for the functions AddInDayHasElapsed,
AddInSecondsHaveElapsed, and AddInMinutesHaveElapsed to work properly.  In
addition, to ensure that "tell <taskname> quit" is processed
properly and that a console operator does not have to wait for an extended
period for a task to terminate, any other "delay" or
"sleep" functions should not impose a delay of more than 5 seconds. 
Developers of server add-ins are responsible for checking the server status
every 5 seconds to see if it is time to quit for every add-in. Using a single
add-in task to do the checking and passing that info along to other processes
is not sufficient as some process aren't responding to requests to dump memory
or to terminate.  

  

Use AddInShouldTerminate to test for the termination condition without
suspending the calling task or returning control to Domino.


 


If you are
writing messages to the Domino Server or Notes client log file, then you should
call AddInIdle or AddInIdleDelay on a regular bases.  This will flush log
entries from memory to disk and will free up memory.


 


**Parameters :**




Output :  

(routine)  -  TRUE if addin should terminate, FALSE if OK to continue  

  

  




 **Sample Usage :**


while (!AddInIdle())  

{  

  /\* Default idle in task stats \*/  

  AddInSetStatus(MSG\_SMKADDN\_IDLE, 0L);  

  

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

                                          item\_name,


                                         
error\_msg))  

      goto Exit;  

  }  

  else if (AddInMinutesHaveElapsed(1))  

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

      /\* There might be serveral minutes worth of import    \*/  

      /\* activity initiated here and AddInShouldTerminate() \*/  

      /\* calls could be blended in among buffered I/O calls \*/  

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

}


 **See Also :**


**[AddInDayHasElapsed](AddInDayHasElapsed.md)**


**[AddInMain](AddInMain.md)**


**[AddInMinutesHaveElapsed](AddInMinutesHaveElapsed.md)**


**[AddInSecondsHaveElapsed](AddInSecondsHaveElapsed.md)**


**[AddInShouldTerminate](AddInShouldTerminate.md)**


**[AddInIdleDelay](AddInIdleDelay.md)**



----------------------------------------------------------------------------------------------------------


 





