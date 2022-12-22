




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




 


**Function : Statistics Reporting**



**StatTraverse** **- Traverse
the statistic(s) for one or more facilities.**


**----------------------------------------------------------------------------------------------------------**



**#include <stats.h>**



void
LNPUBLIC **StatTraverse(**  

      char far \*Facility,  

      char far \*StatName,  

      STATTRAVERSEPROC  Routine,  

      void far \*Context**);**



**Description :**



This
function traverses one or more statistics for one or more facilities.  It calls
a user defined routine, called a traversal routine, for each statistic found.


 


**Parameters :**



Input :  

Facility  -  Name of facility (NULL for all facilities).  See Symbolic Value,
STATPKG\_xxx for a list of facilities monitored by Domino.  

  

StatName  -  Name of statistic (NULL for all statistics).  

  

Routine  -  Pointer to the user defined traversal routine.  This routine is
called once for each statistic found.  

  

The definition of STATTRAVERSEPROC is:  

  

STATUS (LNCALLBACKPTR Routine)  

                    (void far \*Context,         /\* Pointer to data passed to  

                                                                  StatTraverse
to be given to this routine \*/  

                      char far \*Facility,         /\* Facility name \*/  

                      char far \*StatName,    /\* Name of statistic \*/  

                      WORD ValueType,     /\* Value type of the statistic:  

                                                                     VT\_LONG,
VT\_TEXT,  

                                                                    
VT\_TIMEDATE, VT\_NUMBER \*/  

                      void far \*Value);          /\* Value of the statistic \*/  

  

If the traversal routine returns an error, the traversal stops.  

  

Context  -  The traversal routine context block - a pointer to data to be sent
to the user defined traversal routine.  

  




Output :  

(routine)  -  None  

  

  




 **Sample Usage :**


  

StatTraverse(FacilTable[i],        /\* name of facility \*/  

             NULL,                 /\* traverse all stats \*/  

             DisplayTrav,          /\* callback function \*/  

             (void \*)&hCompound);  /\* param passed to callback  

                                      function \*/  

  




 **See Also :**


**[STATPKG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0032008100D8000685256678006EADD9)**


**[StatQuery](StatQuery.md)**


**[StatToText](StatToText.md)**



----------------------------------------------------------------------------------------------------------


 





