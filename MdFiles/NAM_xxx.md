




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




 


**Symbolic Value : Menu Add-In**



**NAM\_xxx** **-** Return
values for the entry point of a Notes menu add-in program.


**----------------------------------------------------------------------------------------------------------**



**#include <addinmen.h>**


 **Symbolic Values :**      NAM\_NOERROR      -  Return value for NAMM\_INITMENU,
NAMM\_COMMAND, and NAMM\_TERM message - no error.  

  

      NAM\_INIT\_CONTINUE         -  Possible return value for NAMM\_INIT message.
Requests Notes to send NAM\_INIT again so that the menu add-in can add another
menu item.  

  

      NAM\_INIT\_STOP     -  Possible return value for NAMM\_INIT message. Tells
Notes that this menu add-in program has no more menu items to add.  

  




**Description :**



These are
the possible return values for the entry point of a Notes menu add-in program.


 **See Also :**


**[NAMM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/006E007C005700A585255DEA0077E6DB)**



----------------------------------------------------------------------------------------------------------


 





