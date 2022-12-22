




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Data Type : Events**



**EVENT\_DATA** **-** Data
structure used by the event handling routines.


**----------------------------------------------------------------------------------------------------------**



**#include
<event.h>**



**Definition :**



typedef struct     {


           DWORD
Links[3];                       /\* Reserved - used to link this struct onto
queues \*/


           char
OriginatingServerName[MAXUSERNAME]; /\* Server name (only if event relayed to
another server) \*/


           WORD
Version;                 /\* EVENT\_VERSION \*/


           WORD
ErrorCode;                       /\* Error code (any values) associated with
this event \*/


           WORD
AdditionalErrorCode;     /\* Additional Error code (any values) associated with
this event \*/


           WORD
AddinNameLength;         /\* Length of AddinName at end of structure \*/


           WORD Type;                            /\*
EVT\_xxx \*/


           WORD
Severity;                /\* SEV\_xxx \*/


           TIMEDATE
EventTime;           /\* Time/date event was generated \*/


           WORD
FormatSpecifier;         /\* FMT\_xxx (format of event data which follows) \*/


           WORD
EventDataLength;         /\* Length of event data which follows \*/


           BYTE
EventSpecificData;               /\* (First byte of) Event Data which follows...
\*/


                                                 /\*
(AddinName string follows...) \*/


    } EVENT\_DATA;


 


**Description :**



This data
structure contains all the data necessary to define an event.  A handle to an
EVENT\_DATA structure is returned as output by the function EventQueueGet.


 **See Also :**


**[EventDeregisterEventRequest](EventDeregisterEventRequest.md)**


**[EventGetDestName](EventGetDestName.md)**


**[EventQueueAlloc](EventQueueAlloc.md)**


**[EventQueueFree](EventQueueFree.md)**


**[EventQueueGet](EventQueueGet.md)**


**[EventQueuePut](EventQueuePut.md)**


**[EventRegisterEventRequest](EventRegisterEventRequest.md)**


**[EVT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00EB004E00DC007F85255E8A0077FF23)**


**[SEV\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00D0001E0008006E85255E8A0077FF24)**



----------------------------------------------------------------------------------------------------------


 





