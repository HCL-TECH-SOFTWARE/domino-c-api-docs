




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



**Data Type : Message Queues;
Statistics Reporting**



**SERVER\_MSG\_BLOCK** **-** Collector
message queue server message structure.


**----------------------------------------------------------------------------------------------------------**



**#include
<stats.h>**



**Definition :**



typedef struct {  

   DWORD  Task;                       /\* Task to be processed by


                              
          collector


                                        
(i.e., Add server) \*/  

   DWORD  Interval;                   /\* Interval to return info in


                                        
minutes \*/  

   char   StatName[MAXSPRINTF];       /\* REMOVE \*/  

   char   StatServerName[MAXPATH];    /\* Name of server that you


                                        
want info about \*/  

   char   MonitorServerName[MAXPATH]; /\* If remote provide proxy


                             
           server name otherwise


                                        
NULL \*/  

   DWORD  MonitorFlags;               /\* Flags passed to monitor


                                        
(Reports, Alarms, ...) \*/  

   DHANDLE hTaskList;                  /\* List of user defined tasks


                                        
to monitor \*/  

   DWORD  TaskListLen;                /\* Size of stat list \*/  

   DHANDLE hStatList;                  /\* List of stats to return to


                                        
monitor \*/  

   DWORD  StatListLen;                /\* Size of stat list \*/  

   char   QueueName[20];              /\* Used by remote collector


                                        
to pass info to proxy


                                        
collector \*/  

} SERVER\_MSG\_BLOCK;


 


**Description :**



This is the
structure of a message that can be put into the collection message queue
(COLLECT\_QUEUE\_NAME in stdnames.h).


 


            DWORD     Task                                              The
Collector Daemon task that is requested.  See xxx\_TASK.


            DWORD     Interval                                           The
interval to return information in minutes.


            char           StatName[MAXSPRINTF]                Statistics
name in the form FacilityName.StatName.  For example, "Server.Users".


            char           StatServerName[MAXPATH]           Name
of the server that you want information about.


            char           MonitorServerName[MAXPATH]      If
Collection server is remote, provide poxy server name, otherwise set to NULL.


            DWORD     MonitorFlags                                  Reserved. 
Must be set to 0.


            DHANDLE  hTaskList                                       Reserved. 
Must be set to NULLHANDLE.


            DWORD
    TaskListLen                                    Reserved.  Must be set to 0.


            DHANDLE  hStatList                                         Reserved. 
Must be set to NULLHANDLE.


            DWORD     StatList
Len                                     Reserved.  Must be set to 0.


            char           QueueName[20]                              Used
by remote collector to pass information to proxy collector.  Otherwise set to
NULL.


            


            


 **See Also :**


**[MQGet](MQGet.md)**


**[MQPut](MQPut.md)**


**[STAT\_RETURN\_BLOCK](STAT_RETURN_BLOCK.md)**


**[xxx\_TASK](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/B3EA7BE45546D1F085256628004A271C)**



----------------------------------------------------------------------------------------------------------


 





