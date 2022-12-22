




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



**ASSISTTRIGGER\_TYPE\_xxx** **-** ODS\_ASSISTSTRUCT
- wTriggerType values for agent trigger types.


**----------------------------------------------------------------------------------------------------------**



**#include <queryods.h>**


 **Symbolic Values :**      ASSISTTRIGGER\_TYPE\_NONE       -  No trigger type; the agent
is unavailable.  

  

      ASSISTTRIGGER\_TYPE\_SCHEDULED        -  Launch according to time schedule.  

  

      ASSISTTRIGGER\_TYPE\_NEWMAIL             -  Launch when new mail delivered.  

  

      ASSISTTRIGGER\_TYPE\_PASTED   -  Launch when documents pasted into
database.  

  

      ASSISTTRIGGER\_TYPE\_MANUAL   -  Launch when requested by user (manually executed).  

  

      ASSISTTRIGGER\_TYPE\_DOCUPDATE       -  Launch when document is updated.  

  

      ASSISTTRIGGER\_TYPE\_SYNCHNEWMAIL             -  Synchronous new mail agent
executed by router.  

  

      ASSISTTRIGGER\_TYPE\_EVENT     -  When an server event executes.  

  




**Description :**



These constants
are used in the wTriggerType field of the ODS\_ASSISTSTRUCT record to determine
the schedule for the agent.  Note that because there are different types of
schedules, the meaning of the fields in the structure is sometimes ambiguous.
Use the following rules:


 


When
wTriggerType == ASSISTTRIGGER\_TYPE\_SCHEDULED:  

        This trigger type means that the agent should run based on a timed
schedule.


 


        wSearchType:
Any of the following are valid: ASSISTSEARCH\_TYPE\_ALL, TYPE\_NEW, and


                       TYPE\_MODIFIED.


 


        wIntervalType:
This is the type of interval: minutes, days, etc.  

                       Any of the following are valid:
ASSISTINTERVAL\_TYPE\_MINUTES, TYPE\_DAYS, TYPE\_WEEK,


                       TYPE\_MONTH.


 


        wInterval:
This is the interval with which the agent will run.  

                       This number is expressed in units of iIntervalType. For
example, if iIntervalType == TYPE\_DAYS,


                       and
iInterval is 2, then the assistant will execute once every two days.


 


        dwTime1
and dwTime2: These variables depend on iIntervalType:  

                       Note: Time of day units are TICKS since midnight GMT


                       (i.e.,
2AM would be 2 \* 60 \* TICKS\_PER\_MINUTE)


 


                       ASSISTINTERVAL\_TYPE\_MINUTES:
dwTime1 and dwTime2 represent the starting and


                       ending
times of the days during which the agent will run. For example, if iInterval is
30, dwTime1


                       is
2PM and dwTime2 is 11PM, then the agent will run every 30 minutes starting at
2PM until


                       11PM.
If the fNoWeekends flag is set, then the agent will not run on weekends. If
dwTime1 is 0


                       and
dwTime2 is TICKS\_IN\_DAY, then it means that the agent should run all day.


 


                       ASSISTINTERVAL\_TYPE\_DAYS:
dwTime1 represents the time of the day at which the


                       agent
will run. If the fNoWeekends flag is set, then the agent will not run on
weekends.


 


                       ASSISTINTERVAL\_TYPE\_WEEK:
dwTime1 represents the time of the day at which the


                       agent
will run; dwTime2 represents the day of the week (1-7) on which it will run.
For example, if  

                       dwTime1 is 10pm and dwTime2 is 4, then the agent will
run once a week on Wednesday at


                       10pm.
The fNoWeekends flags is ignored.


 


                       ASSISTINTERVAL\_TYPE\_MONTH:
dwTime1 represents the time of the day on which the


                       agent
will run; dwTime2 is the day of the month (1-31). For example, if dwTime1 is
5pm and


                       dwTime2
is 27, then the agent will run once per month on the 27th at 5PM. The
fNoWeekends


                       flags
is ignored.


 


wTriggerType
== ASSISTTRIGGER\_TYPE\_NEWMAIL:  

        This tigger type means that the agent should run whenever new mail is
delivered, there are no time


        constraints.


 


        iSearchType:
This parameter is ignored since we always operate on new documents.


 


wTriggerType
== ASSISTTRIGGER\_TYPE\_DOCUPDATE:  

        This tigger type means that the agent should run whenever a data class
document is updated (via


        NSFNoteUpdate)
in the indicated database, there are no time constraints.


 


        wSearchType:
This value is ignored since we always operate on new documents.


 


wTriggerType
== ASSISTTRIGGER\_TYPE\_PASTED:  

        This trigger type means that the agent should run when documents are
pasted (through the UI) into the


        database.


 


        wSearchType:
This value is ignored since we always operate on new documents.


 


wTriggerType
== ASSISTTRIGGER\_TYPE\_MANUAL:  

        This trigger type may only be run through the UI.


 


        wSearchType:
The following are valid: ASSISTSEARCH\_TYPE\_SELECTED, TYPE\_VIEW, TYPE\_ALL,


                       TYPE\_UNREAD,
TYPE\_PROMPT, TYPE\_UI.


 **See Also :**


**[ODS\_ASSISTSTRUCT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/540A215A94BACC0385256261006222BC)**



----------------------------------------------------------------------------------------------------------


 





