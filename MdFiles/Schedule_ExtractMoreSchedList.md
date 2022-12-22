




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



**Schedule\_ExtractMoreSchedList** **- Extract
more schedule list information.**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **Schedule\_ExtractMoreSchedList(**  

      HCNTNR  hCntnr,  

      HCNTNROBJ  hMoreCtx,  

      TIMEDATE\_PAIR FAR \*pInterval,  

      DWORD FAR \*retdwSize,  

      DHANDLE FAR \*rethSchedList,  

      HCNTNROBJ FAR \*rethMore**);**



**Description :**



This
retrieves more schedule list information.


 


**Parameters :**



Input :  

hCntnr  -  The handle to the container of the schedule.  

  

hMoreCtx  -  The handle to more schedule list information that was returned by
previous calls to Schedule\_ExtractMoreSchedList and Schedule\_ExtractSchedList.   

  




Output :  

(routine)  -  NOERROR - Successfully extracted more schedule list information.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

pInterval  -  Point to where the interval of the schedule is returned.  

  

retdwSize  -  Points to where the size of the range is returned.  

  

rethSchedList  -  Points to where a handle to the schedule list associated with
this schedule object is returned. Callers must free this when they're done.  

  

rethMore  -  If not NULLCNTNROBJ then this is the handle to more schedule list
information.  

  




 **See Also :**


**[Schedule\_ExtractMoreSchedList](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/F4DB02C55DAF2FBE482573FB00323559)**



----------------------------------------------------------------------------------------------------------


 





