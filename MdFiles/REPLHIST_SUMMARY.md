




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



**Data Type : Replica Info;
Replication**



**REPLHIST\_SUMMARY** **-** Replication
history summary structure in the array returned from NSFDbGetReplHistorySummary


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdb.h>**



**Definition :**



typedef struct {


        TIMEDATE       ReplicationTime;       /\*      Time
returned from last replciation \*/


        WORD           AccessLevel;           /\*      Access
level at time of replication \*/


        WORD           AccessFlags;           /\*      Access
flags at time of replication \*/


        WORD           Direction;             /\*      NEVER,
SEND, RECEIVE \*/


        DWORD          ServerNameOffset;      /\*      Server
name offset in packed data \*/


        WORD           ServerNameLength;      /\*      Server
name length in packed data \*/


        WORD           FileNameLength;        /\*      File
name length in packed data \*/


                                             /\*      Total
server!!file length is \*/ 


                                             /\*      ServerNameLength
+ FileNameLength + 2 \*/


                                             /\*      to
compensate for the !! separator \*/


        WORD           MoreInfo;              /\*      contains
MoreInfo from cache - includes complete replication flag \*/


        WORD           wSpare;        /\*      Room
for growth \*/


        DWORD          dwSpare;               /\*      Room
for growth \*/


                                             /\*      Server/file
name pairs follow as \*/


                                             /\*      "<server
name>!!<file name>" with \*/


                                             /\*      NULL
after each pairing \*/


}
REPLHIST\_SUMMARY;


 


**Description :**



This
structure is returned by NSFDbGetReplHistorySummary().  NSFDbGetReplHistorySummary()
returns an array of REPLHIST\_SUMMARY structures followed by the packed server
and database filename data.  This data is in the format, <server
name>!!<database filename>, with a NULL terminator at the end of the
database filename.  Use the NSFGetSummaryServerNamePtr() and
NSFGetSummaryFileNamePtr() macros for accessing the packed data following the
REPLHISTORY\_SUMMARY array.  


 **See Also :**


**[NSFGetSummaryFileNamePtr](NSFGetSummaryFileNamePtr.md)**


**[NSFGetSummaryServerNamePtr](NSFGetSummaryServerNamePtr.md)**


**[NSFDbGetReplHistorySummary](NSFDbGetReplHistorySummary.md)**



----------------------------------------------------------------------------------------------------------


 





