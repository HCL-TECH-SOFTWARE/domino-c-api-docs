




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




**Initial Release 4.0**



**Data Type : Agents**



**ODS\_ASSISTSTRUCT** **-** Control
information for an Agent.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WORD     wVersion;      /\* Structure version \*/


   WORD    
wTriggerType;  /\* Type of trigger \*/  

   WORD     wSearchType;   /\* Type of search \*/  

   WORD     wIntervalType; /\* Type of interval \*/  

   WORD     wInterval;     /\* Interval \*/  

   DWORD    dwTime1;       /\* depends on interval type \*/  

   DWORD    dwTime2;       /\* depends on interval type \*/


   TIMEDATE
StartTime;     /\* Agent does not run before this time \*/  

   TIMEDATE EndTime;       /\* Agent does not run after this time \*/


   DWORD    dwFlags;


   DWORD   
dwSpare[16];  

} ODS\_ASSISTSTRUCT;


 


**Description :**



This record
contains the control information for an Agent.  The control information
specifies what events cause the agent to be run, and what times the agent is
run.  The fields in this structure are:


 


wVersion                      Version
of this structure. Only 0 is currently supported.


wTriggerType               Type
of trigger (see ASSISTTRIGGER\_TYPE\_xxx).


wSearchType               Type
of search (see ASSISTSEARCH\_TYPE\_xxx).


wIntervalType               Type
of interval (see ASSISTINTERVAL\_TYPE\_xxx).


wInterval                      Interval; 
interpretation depends on the interval type.


dwTime1                      Interval
time 1;  interpretation depends on the interval type.


dwTime2                      Interval
time 2;  interpretation depends on the interval type.


StartTime                     Agent
does not run before this time.


EndTime                       Agent
does not run after this time.


dwFlags                       Flags
(see ASSISTODS\_FLAG\_xxx).


dwSpare                       Reserved; 
must be 0.


 


The interval
type determines how the wInterval, dwTime1, and dwTime2 fields are
interpreted;  please see the reference entry for ASSISTINTERVAL\_TYPE\_xxx for
details.


 **See Also :**


**[ASSISTODS\_FLAG\_xxx](ASSISTODS_FLAG_xxx.md)**


**[ASSISTSEARCH\_TYPE\_xxx](ASSISTSEARCH_TYPE_xxx.md)**


**[ASSISTTRIGGER\_TYPE\_xxx](ASSISTTRIGGER_TYPE_xxx.md)**


**[ASSISTINTERVAL\_TYPE\_xxx](ASSISTINTERVAL_TYPE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





