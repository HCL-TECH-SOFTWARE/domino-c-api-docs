




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



**NAM\_IN\_xxx** **-** Notes menu
add-in context flags.


**----------------------------------------------------------------------------------------------------------**



**#include <addinmen.h>**


 **Symbolic Values :**      NAM\_IN\_DESK         -  In the desktop.  

  

      NAM\_IN\_VIEW         -  In a view.  

  

      NAM\_IN\_VIEW\_DESIGN      -  Designing a view.  

  

      NAM\_IN\_EDIT\_RO   -  In a read-only document.  

  

      NAM\_IN\_EDIT\_RW   -  In a document - edit mode.  

  

      NAM\_IN\_EDIT\_DESIGN       -  Designing a document.  

  




**Description :**



These flags
specify the current context when a menu add-in program is invoked.  This
information is received by the menu add-in in the NAM\_CONTEXT\_DATA structure
when processing the NAMM\_COMMAND message from Notes.


 **See Also :**


**[NAM\_CONTEXT\_DATA](NAM_CONTEXT_DATA.md)**


**[NAM\_COMMAND\_INFO](NAM_COMMAND_INFO.md)**


**[NAMM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/006E007C005700A585255DEA0077E6DB)**



----------------------------------------------------------------------------------------------------------


 





