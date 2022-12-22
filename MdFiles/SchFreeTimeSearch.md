




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



**Function : Calendaring and
Scheduling**



**SchFreeTimeSearch** **- Search
for free time periods.**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **SchFreeTimeSearch(**  

      const UNID FAR \*pApptUnid,  

      TIMEDATE FAR \*pApptOrigDate,  

      WORD  fFindFirstFit,  

      DWORD  dwReserved,  

      TIMEDATE\_PAIR FAR \*pInterval,  

      WORD  Duration,  

      LIST FAR \*pNames,  

      HANDLE FAR \*rethRange**);**



**Description :**



This routine
searches the schedule database (locally or on a specified server) for free time
periods common to a specified list of people.


 


**Parameters :**



Input :  

pApptUnid  -  This is the UNID of an appointment to ignore for the purposes of
calculating free time. This is useful when you need to move an appointment to a
time which overlaps it.  

  

pApptOrigDate  -  This is the date of the original date of the appointment to
ignore for free time calculations. Note that the only reason that this is here
is for compatibility with Organizer 2.x gateway.  

  

fFindFirstFit  -  If this value is equal to TRUE then this routine will return
just the first free time interval that fits the duration. The size of this
interval will equal to duration.  

  

dwReserved  -  Reserved for future use.  Must be set to 0L.  

  

pInterval  -  Pointer to a TIMEDATE\_PAIR structure that specifies the range
over which the free time search should be performed. In typical scheduling
applications, this might be a range of 1 day or 5 days.  

  

Duration  -  How much free time you are looking for, in minutes.  

  

pNames  -  Pointer to a list of distinguished names whose schedule should be
searched. This list is in TEXT\_LIST format without the datatype word. This list
can be conveniently built with the textlist package (e.g. List Allocate)  

  




Output :  

(routine)  -  NOERROR - Successfully searched for free time.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

rethRange  -  Handle for the RANGE of timedate pairs indicating runs of free
time.  

  




 **See Also :**


**[Schedule\_ExtractFreeTimeRange](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0590897DEE4AE69E482573FB003235C6)**



----------------------------------------------------------------------------------------------------------


 





