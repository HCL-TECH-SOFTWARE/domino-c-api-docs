




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



**Data Type : Calendaring and
Scheduling**



**SCHEDULE** **-** Data
structure for a schedule.


**----------------------------------------------------------------------------------------------------------**



**#include
<schedule.h>**



**Definition :**



typedef struct {


   DWORD        
reserved[8];  

   DBID          dbReplicaID;      /\* Users mail file replica ID \*/  

   TIMEDATE\_PAIR Interval;         /\* events etc. are in this


                                     
interval \*/  

   DWORD         dwErrGateway;     /\* gateway error retrieving this


                                     
schedule \*/  

   STATUS        error;            /\* error retrieving this


                                     
schedule \*/  

   WORD          wReserved;        /\* unused at this time \*/  

   WORD          wOwnerNameSize;   /\* size of owner name


                                     
(includes term.) \*/  

/\* followed by owner name \*/  

} SCHEDULE;


 


**Description :**



Data
structure for a schedule.


 **See Also :**


**[SchContainer\_GetFirstSchedule](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4E45B57B3215216B482573FB003235A6)**


**[SchContainer\_GetNextSchedule](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1693AF3FEEDB673C482573FB00323571)**


**[SchContainer\_FindSchedule](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2E4FE2D9B7788C5A8525635D006E1F86)**



----------------------------------------------------------------------------------------------------------


 





