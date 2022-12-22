




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




 


**Data Type : Replica Info**



**DBREPLICAINFO** **-** Identifies
and configures a replica database.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {  

   TIMEDATE ID;      /\* ID that is same for all replica files \*/  

   WORD     Flags;   /\* Replication flags \*/  

   WORD     CutoffInterval; /\* Automatic Replication Cutoff  

                        Interval (Days) \*/  

   TIMEDATE Cutoff;  /\* Replication cutoff date \*/  

} DBREPLICAINFO;


 


**Description :**



This is the
structure that identifies a replica database and stores the replication options
that affect how the Server's Replicator Task will manipulate the database. 
Some replication Flags, CutoffInterval, and Cutoff members correspond to the
edit controls in the the Workstation's Replication Settings dialog box (in the
File, Database, Properties InfoBox).  

  

The Replica ID is a TIMEDATE structure that contains the time/date of the
replica's creation, used to uniquely identify the database replicas to each
other.  This time/date is NOT normalized to Greenwich Mean Time (GMT), as
keeping the local time zone and daylight savings time settings will further
ensure that it is a unique time/date.


 **See Also :**


**[NSFDbReplicaInfoGet](NSFDbReplicaInfoGet.md)**


**[NSFDbReplicaInfoSet](NSFDbReplicaInfoSet.md)**


**[REPLFLG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255BB3006EBCC0)**



----------------------------------------------------------------------------------------------------------


 





