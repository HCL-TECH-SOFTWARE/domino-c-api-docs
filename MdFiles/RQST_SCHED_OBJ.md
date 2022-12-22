




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



**RQST\_SCHED\_OBJ** **-** Scheduling
Reply/Request object.


**----------------------------------------------------------------------------------------------------------**



**#include
<schgtw.h>**



**Definition :**



typedef struct {


   DWORD        
dwOptions;        /\* see SCHRQST\_xxx \*/  

   WORD          wNumHops;         /\* number of hops so far \*/  

   TIMEDATE\_PAIR Interval;         /\* interval \*/  

   UNID          ApptUnid;         /\* Unid of appt to ignore


                                     
busytime for \*/  

   TIMEDATE      ApptOrigDate;     /\* (Orginizer 2.x) the orig date


                                     
of ignored appt \*/  

   DWORD         reserved[10];  

   WORD          wClientNamesSize; /\* queryer's name length


                                     
(includes term.) \*/  

   WORD          wServerNameSize;  /\* Lotus Domino Server name length


                                     
(includes term.) \*/  

/\*  Followed by Client name doing the query (NULL terminated) \*/  

/\*  Followed by name of Lotus Domino Server to forward this request to


  (NULL terminated). \*/  

} RQST\_SCHED\_OBJ;


 


**Description :**



Scheduling
Reply/Request object.


 **See Also :**


**[SCHRQST\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/619DE548C731AFEB8525635D00797CEC)**


**[SchContainer\_GetRequest](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/133E592859D0BDAD482573FB003235D7)**



----------------------------------------------------------------------------------------------------------


 





