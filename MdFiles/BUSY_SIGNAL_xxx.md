




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




 


**Symbolic Value : Signal Handler**



**BUSY\_SIGNAL\_xxx** **-** Busy signal
handler specific definitions.


**----------------------------------------------------------------------------------------------------------**



**#include <ossignal.h>**


 **Symbolic Values :**      BUSY\_SIGNAL\_FILE\_INACTIVE       -  Remove the "File
Activity" indicator  

  

      BUSY\_SIGNAL\_FILE\_ACTIVE          -  Display the "File Activity"
indicator (not supported on all platforms)  

  

      BUSY\_SIGNAL\_NET\_INACTIVE       -  Remove the "Network Activity"
indicator.  

  

      BUSY\_SIGNAL\_NET\_ACTIVE          -  Display the "Network
Activity" indicator.  

  

      BUSY\_SIGNAL\_POLL           -  Display the "Poll" indicator.  

  

      BUSY\_SIGNAL\_WAN\_SENDING      -  Display the "Wan Sending"
indicator.  

  

      BUSY\_SIGNAL\_WAN\_RECEIVING   -  Display the "Wan Receiving"
indicator.  

  




**Description :**



These
symbolic constants identify the type of busy signal indicator that is to be
painted on the screen when the busy signal handler function (OS\_SIGNAL\_BUSY) is
called.


 **See Also :**


**[OSSIGBUSYPROC](OSSIGBUSYPROC.md)**


**[OS\_SIGNAL\_xxx](OS_SIGNAL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





