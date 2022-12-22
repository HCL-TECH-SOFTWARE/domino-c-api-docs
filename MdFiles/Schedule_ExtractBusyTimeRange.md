




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



**Schedule\_ExtractBusyTimeRange** **- Retrieve
a RANGE from a schedule.**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **Schedule\_ExtractBusyTimeRange(**  

      HCNTNR  hCntnr,  

      HCNTNROBJ  hSchedObj,  

      const UNID FAR \*punidIgnore,  

      TIMEDATE\_PAIR FAR \*pInterval,  

      DWORD FAR \*retdwSize,  

      DHANDLE FAR \*rethRange,  

      HCNTNROBJ \*rethMoreCtx**);**



**Description :**



This routine
retrieves a RANGE from a schedule that specifies all a users' busy times. It
returns a handle to the memory where the range has been placed.  Note:
submitting a range or time that is in the past is not supported.


 


**Parameters :**



Input :  

hCntnr  -  The handle to the container of the schedule.  

  

hSchedObj  -  the HCNTROBJ of the schedule object  

  

punidIgnore  -  Points to the UNID to ignore in busy time calculations  

  




Output :  

(routine)  -  NOERROR - Successfully extracted busy time range.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

pInterval  -  Points to where we return the overall interval of the schedule  

  

retdwSize  -  The size of the range returned.  

  

rethRange  -  Points to where we return a handle to the time range associated
with this schedule. Note: Callers must free this when they're done.  

  

rethMoreCtx  -  If not NULLCNTNROBJ, then this is the handle to more busy time
information. This handle is passed to Schedule\_ExtractMoreBusyTimeRange()  

  




 **Sample Usage :**


    /\* Extract the busy
times \*/  

    if (error = Schedule\_ExtractBusyTimeRange(rethCntnr, hSchedObj,
&theApptUnid, &pInterval, &retdwSize, &rethRange,
&hMoreObj))


               LAPI\_RETURN
(ERR(error));


 **See Also :**


**[Schedule\_ExtractFreeTimeRange](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/0590897DEE4AE69E482573FB003235C6)**


**[Schedule\_ExtractMoreBusyTimeRange](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/99FFCB1AF4908A5B482573FB00323568)**



----------------------------------------------------------------------------------------------------------


 





