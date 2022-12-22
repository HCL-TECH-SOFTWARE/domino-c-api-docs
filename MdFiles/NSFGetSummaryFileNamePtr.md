




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



**Function : Replica Info; Replication**



**NSFGetSummaryFileNamePtr** **- Returns
the database filename for a specific entry in the replication history summary.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



char
FAR \* **NSFGetSummaryFileNamePtr(**  

      REPLHIST\_SUMMARY \*Summary,  

      DWORD  Index**);**



**Description :**



This routine
returns the database filename for a specific entry in the replication history
summary data.  Use NSFDbGetReplHistorySummary() to obtain a handle to the
replication history summary data.  Use OSLock() to lock this handle to obtain a
pointer to the data.  Pass this pointer in as the Summary argument of this
routine.


 


This routine
is implemented as a macro:


 


#define
NSFGetSummaryFileNamePtr(Summary, Index) \  

   (((char FAR \*) Summary) + Summary[Index].ServerNameOffset + \  

                             Summary[Index].ServerNameLength + 2)


 


**Parameters :**



Input :  

Summary  -  Pointer to the first structure in the replication history summary
data.  

  

Index  -  Index into the replication history summary array.  This index is
zero-based and indicates which entry in the replication history summary you
wish to access.  

  




Output :  

(routine)  -  A null-terminated pointer to the database filename component of a
replication history summary entry.  

  

  




 **See Also :**


**[NSFDbGetReplHistorySummary](NSFDbGetReplHistorySummary.md)**


**[NSFGetSummaryServerNamePtr](NSFGetSummaryServerNamePtr.md)**


**[REPLHIST\_SUMMARY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FA9B950A1164D5EC85256379006EF14A)**



----------------------------------------------------------------------------------------------------------


 





