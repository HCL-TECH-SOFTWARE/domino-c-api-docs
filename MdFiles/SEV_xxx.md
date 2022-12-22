




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : Events**



**SEV\_xxx** **-** Describes
the severity of a user-generated event.


**----------------------------------------------------------------------------------------------------------**



**#include <event.h>**


 **Symbolic Values :**      SEV\_UNKNOWN      -  The severity of the event is unknown  

  

      SEV\_FATAL             -  This event indicates a fatal condition.  

  

      SEV\_FAILURE          -  This event indicates a failure of some sort.  

  

      SEV\_WARNING1      -  This event serves as a warning (High priority).  

  

      SEV\_WARNING2      -  This event serves as a warning (Low priority).  

  

      SEV\_NORMAL         -  This event signifies that processing is continuing
normally.  

  




**Description :**



These are
the permissible values for the "Severity" member of the EVENT\_DATA
data structure. 


 **See Also :**


**[EVENT\_DATA](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/179DC79145140DED85256A2A0065E34F)**


**[EVT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00EB004E00DC007F85255E8A0077FF23)**



----------------------------------------------------------------------------------------------------------


 





