




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




**Initial Release 4.5**



**Function : Calendaring and
Scheduling**



**Schedule\_ExtractFreeTimeRange** **- Retrieve
a RANGE from a schedule**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **Schedule\_ExtractFreeTimeRange(**  

      HCNTNR  hCntnr,  

      HCNTNROBJ  hSchedObj,  

      const UNID FAR \*punidIgnore,  

      BOOL  fFindFirstFit,  

      WORD  wDuration,  

      TIMEDATE\_PAIR FAR \*pInterval,  

      DWORD FAR \*retdwSize,  

      DHANDLE FAR \*rethRange**);**



**Description :**



This routine
retrieves a free time RANGE from a schedule and returns a handle to the memory
where the range has been placed. It will only return 64k of free time ranges. 
Note: submitting a range or time that is in the past is not supported.


 


**Parameters :**



Input :  

hCntnr  -  The handle to the container of the schedule.  

  

hSchedObj  -  The HCNTNROBJ of the schedule project.  

  

punidIgnore  -  Points to UNID to ignore in busy time calculation.  

  

fFindFirstFit  -  If true then only the first fit is used  

  

wDuration  -  Number of minutes in meeting if fFindFirstFit is True  

  




Output :  

(routine)  -  NOERROR - Successfully extracted free time range.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

pInterval  -  Points to where we return the overall interval of the schedule  

  

retdwSize  -  The size of the range returned  

  

rethRange  -  Points to where we return a handle to the time range associated
with this schedule. Note: callers must free this when they're done.  

  




 **Sample Usage :**


    /\* Get the first
free time available \*/  

    if (error = Schedule\_ExtractFreeTimeRange(rethCntnr, hSchedObj,
&theApptUnid, fFindFirstFit, wDuration, &pInterval, &retdwSize, &rethRange))  

              LAPI\_RETURN (ERR(error));


 **See Also :**


**[SchFreeTimeSearch](SchFreeTimeSearch.md)**



----------------------------------------------------------------------------------------------------------


 





