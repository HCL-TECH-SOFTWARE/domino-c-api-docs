




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




**Initial Release 4.0**



**Function : Statistics Reporting**



**StatReset** **- Set a
numeric-additive statistic to 0.**


**----------------------------------------------------------------------------------------------------------**



**#include <stats.h>**



STATUS
LNPUBLIC **StatReset(**  

      const char \*Facility,  

      const char \*StatName**);**



**Description :**



This
function will set the value of a numeric-additive statistic (a statistic of
type VT\_LONG or VT\_NUMBER and is additive) to 0.  This function performs the
same operation as the Set Stat Domino Server console command.  For more
information on this operation, refer to the *Administering the Domino System*
documentation..


 


**Parameters :**



Input :  

Facility  -  Null-terminated string containing the name of the facility.  

  

StatName  -  Null-terminated string containing the name of the statistic.  

  




Output :  

(routine)  -  Return status from this call:  

  

NOERROR - Success  

  

ERR\_STAT\_NOT\_SET - Unable to set the specified statistic to 0.  

  

ERR\_STAT\_NOT\_FOUND - Statistic is not in the Lotus Domino Server's statistic
table.  

  

ERR\_xxx - Errors returned by lower level Notes functions: (memory management,
file operations, network errors, etc.).  There are so many possible causes,
that it is best to use the code in a call to OSLoadString and display/log the
error for the user as your default error handling.  

  

  




 **See Also :**


**[STATPKG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0032008100D8000685256678006EADD9)**


**[StatTraverse](StatTraverse.md)**


**[StatUpdate](StatUpdate.md)**



----------------------------------------------------------------------------------------------------------


 





