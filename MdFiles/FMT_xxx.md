




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



**FMT\_xxx** **-** EVENT\_DATA -
FormatSpecifier flags.


**----------------------------------------------------------------------------------------------------------**



**#include <event.h>**


 **Symbolic Values :**      FMT\_UNKNOWN      -  Unknown format.  

  

      FMT\_TEXT   -  Text format.  

  

      FMT\_ERROR\_CODE            -  Data is in the form of a STATUS code.  

  

      FMT\_ERROR\_MSG              -  Data is an error message string.  

  




**Description :**



Use one of
these values for the FormatSpecifier member of the EVENT\_DATA structure to
describe the format of the event data that follows the structure.


 **See Also :**


**[EVENT\_DATA](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/179DC79145140DED85256A2A0065E34F)**



----------------------------------------------------------------------------------------------------------


 





