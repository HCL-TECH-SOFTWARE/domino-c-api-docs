




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




**Initial Release 5.0**



**Data Type : Statistics Reporting**



**STAT\_RETURN\_BLOCK** **-** Message
returned by the Collector.


**----------------------------------------------------------------------------------------------------------**



**#include
<stats.h>**



**Definition :**



typedef struct {  

   char   StatName[MAXSPRINTF];                    

   DHANDLE hStatName;                      

   DWORD  StatNameSize;                    

   char   ServerName[MAXPATH];                     

   STATUS error;                                                  

} STAT\_RETURN\_BLOCK;


 


**Description :**



This is the
structure of a message returned by the Collector in a response to a request
made by the application.  The return message is put on the application's
message queue.


 


The
hStatName member of this structure is a formatted buffer containing the
requested statistics information.  See the Message Queues chapter in the *User
Guide* for details on how to parse this buffer.


 **See Also :**


**[MQGet](MQGet.md)**


**[MQPut](MQPut.md)**


**[SERVER\_MSG\_BLOCK](SERVER_MSG_BLOCK.md)**



----------------------------------------------------------------------------------------------------------


 





