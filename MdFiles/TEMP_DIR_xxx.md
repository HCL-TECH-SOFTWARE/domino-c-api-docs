




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




**Initial Release 6**



**Symbolic Value : OS Environment
Variables**



**TEMP\_DIR\_xxx** **-** System temp
directory constants.


**----------------------------------------------------------------------------------------------------------**



**#include <osenv.h>**


 **Symbolic Values :**      TEMP\_DIR\_PREFIX             -  System temporary directory
prefix - "notes".  

  

      TEMP\_DIR\_SUFFIX\_LEN     -  System temporary directory suffix length - 6.
If changing, must change TEMP\_DIR\_SUFFIX\_FORMATSPEC to match.  

  

      TEMP\_DIR\_SUFFIX\_FORMATSPEC            -  System temporary directory
format specification - "%06x".  

  

      TEMP\_DIR\_DEFAULT\_SUFFIX        -  System temporary directory default
suffix - "G00000".  

  

      TEMP\_DIR\_SUFFIX\_MAX\_VALUE    -  System temporary directory suffix maximum
value - 0x00FFFFFF.  

  




 




----------------------------------------------------------------------------------------------------------


 





