




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



**SCHMSG** **-** Scheduling
Request/Reply message structure


**----------------------------------------------------------------------------------------------------------**



**#include
<schgtw.h>**



**Definition :**



typedef struct {     

   DWORD    dwFlags;         /\* Flags (see SCHMSG\_xxx) \*/  

   WORD     wFunction;       /\* function name (see SCHFUNC\_RQST\_xxx) \*/  

   HCNTNR   hMsgCntnr;       /\* handle to a container object \*/  

   STATUS   error;  

   TIMEDATE tdRequestQueued; /\* time request was queued \*/


   DWORD    spare[5];


} SCHMSG;


 


**Description :**



Used by
gateways to pass in scheduling requests.


 **See Also :**


**[MQGet](MQGet.md)**


**[SCHMSG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C9D6C875A5AE4E5F8525635D007F014D)**


**[SCHFUNC\_RQST\_xxx](SCHFUNC_RQST_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





