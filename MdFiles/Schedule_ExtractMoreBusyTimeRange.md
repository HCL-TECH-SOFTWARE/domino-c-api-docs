




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



**Schedule\_ExtractMoreBusyTimeRange** **- Extracts
more busy time information.**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **Schedule\_ExtractMoreBusyTimeRange(**  

      HCNTNR  hCntnr,  

      HCNTNROBJ  hMoreCtx,  

      const UNID \*punidIgnore,  

      TIMEDATE\_PAIR \*pInterval,  

      DWORD \*retdwSize,  

      DHANDLE \*rethRange,  

      HCNTNROBJ \*rethMore**);**



**Description :**



This is the
continuation of the process begun with Schedule\_ExtractBusyTimeRange.


 


**Parameters :**



Input :  

hCntnr  -  The handle to the container of the schedule.  

  

hMoreCtx  -  The handle to more information that we got back from
Schedule\_ExtractBusyTimeRange.  

  

punidIgnore  -  Points to UNID to ignore in busy time calculation.  

  




Output :  

(routine)  -  NOERROR - Successfully extracted busy time range.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

pInterval  -  Points to where we return the overall interval of the schedule.  

  

retdwSize  -  The size of the range returned.  

  

rethRange  -  Points to where we return a handle to the time range associated
with this schedule.  

  

rethMore  -  If not NULLCNTNROBJ then this is the handle to more busytime information.
This handle is passed to Schedule\_ExtractMoreBusyTimeRange.  

  




 **See Also :**


**[Schedule\_ExtractBusyTimeRange](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/D880C3A5D7CB38FE482573FB0032354D)**



----------------------------------------------------------------------------------------------------------


 





