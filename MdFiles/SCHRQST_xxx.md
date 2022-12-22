




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



**Symbolic Value : Calendaring and
Scheduling**



**SCHRQST\_xxx** **-** Option flags
for scheduling.


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**


 **Symbolic Values :**      SCHRQST\_COMPOSITE      -  Return composite schedule.  

  

      SCHRQST\_EACHPERSON   -  Return each person's schedule.  

  

      SCHRQST\_LOCAL   -  Do only local lookup.  

  

      SCHRQST\_FORCEREMOTE            -  Force remote lookups even if
workstation based mail.  

  

      SCHRQST\_EXTFORMAT     -  Get busytime in the SCHED\_ENTRY\_EXT format
instead of the pre-Domino 6 SCHED\_ENTRY format . Note that this flag does not
guarantee that data will be in SCHED\_ENTRY\_EXT format. Pre-Domino 6 busytime
data will remain in SCHED\_ENTRY format. To determine which format is used,
check the Spare member of the SCHED\_LIST structure. If 0, the data is in
SCHED\_ENTRY format, otherwise the data is in SCHED\_ENTRY\_EXT format.  

  




**Description :**



Option flags
used in scheduling API calls such as SchRetrieve.


 **See Also :**


**[SCHED\_LIST](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/77A3B36469FBA9FD85256361004F207C)**


**[SchRetrieve](SchRetrieve.md)**


**[SchSrvRetrieve](SchSrvRetrieve.md)**


**[SchSrvRetrieveExt](SchSrvRetrieveExt.md)**



----------------------------------------------------------------------------------------------------------


 





