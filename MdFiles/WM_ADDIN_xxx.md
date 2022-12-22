




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




 


**Symbolic Value : Add-In DLL**



**WM\_ADDIN\_xxx** **-** Messages a
menu add-In function may send to Notes


**----------------------------------------------------------------------------------------------------------**



**#include <addinmen.h>**


 **Symbolic Values :**      WM\_ADDIN\_FIRST   -  Menu add-in message identifier. This
symbol is used in the definition of the messages a menu add-in may send to
Notes. It is not to be explicitly used by the menu add-in program.  

  

      WM\_ADDIN\_REFRESH        -  Tells Notes to refresh the current view.  

  

      WM\_ADDIN\_IMPORT           -  Tells Notes to import to the editor the CD
scratch file specified in the context block.  

  




**Description :**



Identifiers
that specify messages a menu add-in function may send to the Notes main window.
Use these symbols when calling SendMessage under Windows to specify what
message to send to the Notes window. These messages request Notes to take a
particular action. Menu add-in functions may send these messages to the Notes
main window when processing the NAMM\_COMMAND message.


 **See Also :**


**[NAMM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/006E007C005700A585255DEA0077E6DB)**



----------------------------------------------------------------------------------------------------------


 





