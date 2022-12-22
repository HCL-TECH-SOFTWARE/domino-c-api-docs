




<!--
 /\* Font Definitions \*/
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



**Function : Statistics Reporting**



**StatQueryTime** **- Returns
the specified statistic in a formatted statistics buffer.**


**----------------------------------------------------------------------------------------------------------**



**#include <stats.h>**



STATUS
LNPUBLIC **StatQueryTime(**  

      char far \*Facility,  

      char far \*StatName,  

      char far \*HeaderString,  

      char far \*NamePrefix,  

      char far \*ValuePrefix,  

      char far \*LineSuffix,  

      DHANDLE far \*rethStats,  

      DWORD far \*retStatsLength**);**



**Description :**



This
function traverses the specified statistic or can traverse all statistics and
returns the statistics information in a formatted statistics buffer.  The
information includes the time each statistic was last updated.  This function
is similar to StatQuery.  StatQuery traverses all statistics (you cannot
specify a specific statistic) and does not include the time each statistic was
last updated.


 


**Parameters :**



Input :  

Facility  -  Optional.  Name of facility.  Usee NULL for all facilities.  See
Symbolic Value, STATPKG\_xxx for a list of facilities monitored by Domino.  

  

StatName  -  Optional.  Name of statistic.  Use NULL for all statistics.  

  

HeaderString  -  Optional.  Pointer to a NULL terminated string to be inserted
at the start of the returned buffer.  Use NULL if no string is desired.  

  

NamePrefix  -  Pointer to a NULL terminated string of characters to precede the
statistic name.  

  

ValuePrefix  -  Pointer to a NULL terminated string of characters to precede
the statistics value.   

  

LineSuffix  -  Pointer to a NULL terminated string of characters that will
terminate the statistics value (ie:  "\n").  

  




Output :  

(routine)  -  Return status from this call -- indicates either success
(NOERROR) or what the error is.  An error will stop the traversal.  

  

  

rethStats  -  Handle to the returned formatted statistics buffer.  Use OSLock
to obtain a pointer to this buffer and OSMemFree to release the storage.  The
buffer will be NULL terminated.  

  

retStatsLength  -  Length of data in the returned formatted statistics buffer.  

  




 **See Also :**


**[StatQuery](StatQuery.md)**


**[StatTraverse](StatTraverse.md)**



----------------------------------------------------------------------------------------------------------


 





