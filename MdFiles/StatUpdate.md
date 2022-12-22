




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



**StatUpdate** **- Updates a
statistic's value.**


**----------------------------------------------------------------------------------------------------------**



**#include <stats.h>**



STATUS
LNPUBLIC **StatUpdate(**  

      const char far \*Facility,  

      const char far \*StatName,  

      WORD  Flags,  

      WORD  ValueType,  

      const void far \*Value**);**



**Description :**



This
function updates the value of a statistic for the current server session.  For
information regarding the Lotus Domino server statistics see the *Administering
the Domino System* documentation.


 


**Parameters :**



Input :  

Facility  -  Name of facility.  See Symbolic Value, STATPKG\_xxx for a list of
existing Domino facilities.  If the facility is not an existing facility
monitored by Domino, a new facility with the  accompanying statistic will be
created for the current server session.    

  

StatName  -  Name of statistic.  If the facility and statistic combination is
not one that exists and is monitored by Domino, a new statistic will be created
for the current server session.   

  

Flags  -  Flags that modify the behavior of StatUpdate. Specify 0 for default
behavior. Specify ST\_UNIQUE if only one instance of statistic should be
allowed.  Specify ~ST\_UNIQUE if you want to append another instance of this
statistic.  Specify ST\_ADDITIVE if the value type of the statistic is VT\_LONG
or VT\_NUMBER and you want the new value added to the current value of the
statistic.  

  

ValueType  -  Value type of the statistic:  VT\_LONG, VT\_TEXT, VT\_TIMEDATE, or
VT\_NUMBER.  

  

Value  -  Value of the statistic.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success
(NOERROR) or what the error is.  

  

  




 **Sample Usage :**


  

 nError = StatUpdate (STATPKG\_SERVER,          /\* name of facility \*/  

                      "Administrator",         /\* stat name \*/  

                      ST\_UNIQUE,               /\* stat is unique \*/  

                      VT\_TEXT,                 /\* stat value type \*/  

                      NEW\_SERVER\_ADMINISTRATOR); /\* new name \*/  

  




 **See Also :**


**[StatDelete](StatDelete.md)**


**[STATPKG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0032008100D8000685256678006EADD9)**


**[ST\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00BA003E006D006985255EB4006943AA)**



----------------------------------------------------------------------------------------------------------


 





